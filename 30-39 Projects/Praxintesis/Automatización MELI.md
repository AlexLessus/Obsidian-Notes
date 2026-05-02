### La decisión arquitectónica crítica

Implementar este flujo de 2 pasos (Buscar ID por código de barras -> Consultar ID para sacar el precio del ganador) es súper rápido, estable y 100% nativo. **Pero tiene una limitante:** Solo funciona si los productos de la empresa están dentro del sistema de "Catálogo" de Mercado Libre.

Si la empresa vende productos muy de nicho, artesanales, o publicaciones tradicionales que no compiten por la "Buy Box" (caja de compra principal), este endpoint no nos servirá para ver a todos los competidores dispersos.

Si la necesidad de la empresa es rastrear _todas_ las publicaciones de la competencia, incluso las que no son de catálogo, la única solución viable y profesional será regresar al plan de **Apify**, pero rediseñando el flujo para que sea asíncrono (usando Webhooks) para que n8n no se quede colgado esperando.

Considerando el modelo de negocio de la empresa que estás asesorando, ¿sus productos compiten dentro del sistema de Catálogo oficial de Mercado Libre, o necesitan rastrear publicaciones tradicionales dispersas?

Productos ganadores
API de productos ganadores 8760 precios sku stock?

Extraer datos
sheets
Buscar productos, diferencia de precios, comparar productos
Encontrar categoria del producto

fail

---
API


``` python 
const express = require('express');
const { chromium } = require('playwright-extra');
const stealth = require('puppeteer-extra-plugin-stealth')();

chromium.use(stealth);

const app = express();
app.use(express.json());

app.post('/scrape-ml', async (req, res) => {
    const { keyword } = req.body;
    
    if (!keyword) {
        return res.status(400).json({ error: 'Falta el término de búsqueda' });
    }

    console.log(`\n--- Nueva petición recibida: "${keyword}" ---`);
    let browser;

    try {
        console.log('1. Lanzando navegador...');
        browser = await chromium.launch({ 
            headless: true,
            args: [
                '--no-sandbox',               // OBLIGATORIO en Docker (usuario root)
                '--disable-setuid-sandbox',   // OBLIGATORIO en Docker
                '--disable-dev-shm-usage',    // Evita cuelgues por falta de memoria compartida
                '--disable-gpu'               // Apaga la aceleración gráfica innecesaria
            ]
        });
        
        console.log('2. Navegador listo. Abriendo pestaña...');
        const context = await browser.newContext({
            userAgent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36',
            viewport: { width: 1920, height: 1080 }
        });
        
        const page = await context.newPage();
        const searchUrl = `https://listado.mercadolibre.com.mx/${encodeURIComponent(keyword)}`;
        
        console.log(`3. Navegando a: ${searchUrl}`);
        // Aumentamos un poco el timeout y esperamos a que la red esté casi inactiva
        await page.goto(searchUrl, { waitUntil: 'domcontentloaded', timeout: 45000 });

        console.log('4. Página cargada. Extrayendo datos del DOM...');
        const primerResultado = await page.evaluate(() => {
            const item = document.querySelector('li.ui-search-layout__item');
            if (!item) return null;

            const titulo = item.querySelector('h2.ui-search-item__title')?.innerText || '';
            const precioTexto = item.querySelector('.andes-money-amount__fraction')?.innerText || '0';
            const link = item.querySelector('a.ui-search-item__group__element')?.href || '';
            
            const precio = parseFloat(precioTexto.replace(/,/g, ''));
            return { titulo, precio, link };
        });

        console.log('5. Cerrando navegador...');
        await browser.close();

        if (!primerResultado) {
            console.log('-> Resultado: No se encontraron productos en la página.');
            return res.json({ encontrado: false, mensaje: 'No se encontraron resultados' });
        }

        console.log(`-> Éxito: Encontrado "${primerResultado.titulo}" a $${primerResultado.precio}`);
        return res.json({
            encontrado: true,
            datos: primerResultado
        });

    } catch (error) {
        if (browser) await browser.close();
        console.error('!!! Error durante el scraping:', error.message);
        return res.status(500).json({ error: 'Fallo al procesar la página', detalle: error.message });
    }
});

app.listen(3000, () => console.log('✅ API Scraper de ML lista y escuchando en el puerto 3000'));
```

Re build
``` docker
docker stop scraper_ml
docker rm scraper_ml
docker build -t api-scraper-ml .
docker run -d --name scraper_ml -p 3000:3000 --restart unless-stopped api-scraper-ml
```

Logs
```
docker logs -f scraper_ml
```

#### Autorizar credencial ssh en droplet
```
chmod 700 ~/.ssh && chmod 600 ~/.ssh/authorized_keys
```




---
# Api ML
code=TG-69f4e8a35a828900017c2f58-307047262


```
https://auth.mercadolibre.com.mx/authorization?response_type=code&client_id=6117729713081255&redirect_uri=https://oauth.n8n.cloud/oauth2/callback&code_challenge=$CODE_CHALLENGE&code_challenge_method=$CODE_METHOD
```
https://oauth.n8n.cloud/oauth2/callback
JgQ2MslKFismhDizXGTFULP6wHKUMe3z
6117729713081255


```javascript
https://auth.mercadolibre.com.mx/authorization?response_type=code&client_id=6117729713081255&redirect_uri=https://oauth.n8n.cloud/oauth2/callback
```
TG-69f4f67f4e21cc000171a135-307047262

``` json
{
    "access_token": "APP_USR-6117729713081255-050114-f02b120db5cc810edd6a3c9cd57cbde2-307047262",

    "token_type": "Bearer",

    "expires_in": 21600,

    "scope": "offline_access read urn:global:admin:info:/read-only urn:global:admin:info:/read-write urn:global:admin:oauth:/read-only urn:global:admin:oauth:/read-write urn:global:admin:users:/read-only urn:ml:all:comunication:/read-write urn:ml:all:publish-sync:/read-write urn:ml:mktp:ads:/read-write urn:ml:mktp:comunication:/read-write urn:ml:mktp:invoices:/read-write urn:ml:mktp:metrics:/read-only urn:ml:mktp:offers:/read-write urn:ml:mktp:orders-shipments:/read-write urn:ml:mktp:publish-sync:/read-write urn:ml:vis:comunication:/read-write urn:ml:vis:publish-sync:/read-write write",

    "user_id": 307047262,

    "refresh_token": "TG-69f4f6b1fcf5480001ad5e93-307047262"

}
```


ID_user: 307047262