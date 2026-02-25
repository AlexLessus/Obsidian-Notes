# What is computer vision?
The goal of computer vision is to help computers see and understand the content of digital images. 
Computer vision is necessary to enable, for example, self-driving cars. Manufacturers such as Tesla, BMW, Volvo, and Audi use multiple cameras to acquire images from the environment so that their self-driving cars can detect objects, lane markings, and traffic signs to safely drive.

![[Pasted image 20260213223344.png]]

## Image data
To understand how it works, we first need to find out what image data looks like. An image is made up of pixels. 

These pixels contain information about color and intensity.![[Pasted image 20260213223412.png]]
 *you can see a grayscale pixelated image. Each pixel's intensity can be represented by a number between 0 and 255.*
 
## **But what about colored images?** 
A colored image is generally stored in the RGB system. RGB stands for Red, Green, and Blue. Each image can be thought of as being represented by three rasters, one for each color channel. 
This means that you need three times the amount of data to store a color image compared to a grayscale one. So, digital images can actually be seen as a bunch of numbers. Just like before, these numbers can be used as features for your machine learning model.
![[Pasted image 20260213223534.png]]

## Training the neural network
Don't forget, part of the magic of neural networks is that ==you don't really need to worry about what it is doing in the middle==. 
All you need to do is give it a lot of images of faces, the features, as well as the correct identity, the labels, and during training the learning algorithm will figure out by itself what each of these neurons in the middle should be computing.


# Ejemplo del orden de una red neuronal
En un bar, entablas conversación con alguien que resulta ser un científico de datos del departamento de vehículos autónomos de Tesla. Empieza a hablar de uno de los modelos de aprendizaje profundo que construyó hace un tiempo. Fue capaz de clasificar imágenes de vehículos como coches o camiones. Discutes el proceso y descubres que utilizó una red neuronal para construir el modelo.

¿Puedes colocar los pasos de una red neuronal en el orden correcto?
![[Pasted image 20260213224115.png]]