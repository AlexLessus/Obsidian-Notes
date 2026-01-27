## Main Components
1. @Entity
	Represents a table within the database.
	Room creates a table for each class has ==@Entity== annotation, the fields in the class correspond to columns in the table. 
```	  
	@Entity(tableName = "coffee_logs")  
	data class CoffeeLog(  
	    @PrimaryKey(autoGenerate = true)  
	    val id: Long = 0,  
	    val beanName: String,  
	    val method: String,  
	    val ratio: Float,  
	    val water: Float,  
	    val coffee: Float,  
	    val rating: Int,  
	    val date: Date  
	)
```
1. @Dao
	 DAOs are responsible for defining the methods that access the database. 
	 This is the place where we write our queries.
```
	 @Dao  
	interface CoffeeLogDao {  
	  
	    @Insert  
	    suspend fun insert(coffeeLog: CoffeeLog)  
	  
	    @Update  
	    suspend fun update(coffeeLog: CoffeeLog)  
	  
	    @Delete  
	    suspend fun delete(coffeeLog: CoffeeLog)  
	  
	    @Query("SELECT * FROM coffee_logs ORDER BY date DESC")  
	    fun getAll(): Flow<List<CoffeeLog>>  
	  
	    @Query("SELECT * FROM coffee_logs WHERE id = :id")  
	    fun getById(id: Long): Flow<CoffeeLog>  
	}
```
1. @Database
	 Contains the database holder and serves as the main access point for the underlying connection to your app's data.
```
	 @Database(entities = [CoffeeLog::class], version = 1, exportSchema = false)  
	abstract class AppDatabase : RoomDatabase() {  
	  
	    abstract fun coffeeLogDao(): CoffeeLogDao  
	  
	    companion object {//this will be visible for other classes  
	        @Volatile  
	        private var INSTANCE: AppDatabase? = null  
	  
	        //if there is an instance, return it, otherwise create one  
	        fun getDatabase(context: Context): AppDatabase {  
	            return INSTANCE ?: synchronized(this) {  
	                val instance = Room.databaseBuilder(  
	                    context.applicationContext,  
	                    AppDatabase::class.java,  
	                    "coffee_log_database"  
	                ).build()  
	                INSTANCE = instance  
	                instance  
	            }  
	        }  
	    }  
	}
```


## Repository
==A repository class abstracts access to multiple data sources.==
The repository is not part of the Architecture components libraries, but is a suggested best practice for code separation and architecture

## View Model
The ViewModel's role is to provide data to the UI and survive configuration changes.
A ViewModel acts as a communication center between the Repository and the UI.
