# UCB-Project-2
The Github repository has 3 folders:

1.) Data: containing original dataset vehicles.csv and new datasets I created;


2.) Jupyter Notebooks : containing the 1st Data Cleaning Phase (the 1st file to be opened) and subsequent notebooks: each per type of car;


3.) Reports: containing a report for UCB  and  report for the "client".


For this assignment I assumed that the report I am making is for a national used car dealership (such as Vroom or Carvana) that ships the cars to all states.

Since this is a national dealer I concentrated on types of cars. Anyone buying a car has a particular type of car in mind depending on their needs. A large family might buy a minivan, a contractor might go for a pickup, a student might go for a coup, while a dog owner might want to have a wagon. All these cars have different features that are attractive to a buyer. I also separated cars that are 25+ years old because they are considered antiques by definition. Hence I decided to divide the data into groups by type of the car:
 
 Sedan
 
 SUV
 
 Pickup
 
 Truck
 
 Coupe
 
 Hatchback
 
 Convertible
 
 Van
 
 Wagon
 
 Minivan
 
 Bus
 
 Offroad
 
 Antiques
 
 Convertible
 
 Van

 Wagon
 
 Minivan
 
 Bus
 
 Offroad
 
 Antiques

Since the dealer has a national database and ships the cars to all locations the state and region column/ feature will not be considered in my ML model.

THE PROCESS OF CREATING BEST ML MODEL

Data Understanding & Preparation

After performing EDA I checked for
* missing values, 
* outliers, 
* duplicates, 
* consistency, 
* accuracy, 
* completeness. 
In the process I :
* saw anomalies in pricing and odometer,
* decided that adding 'age' column is more beneficial than having 'year',
* noticed a lot of missing data can be filled based on 'VIN' column value decoding,
* realized some missing values are in the wrong column,
* dropped id column because it didn't contribute to building a model,
* dropped VIN column because values are all unique and don't affect outcomes (after using it to
* fill many missing values ),
* dropped the 'model' column, because it had 30,000 unique values and would just slow down processing time and wouldn't have valuable input,
* dropped the "size" column because more than 70% of data is missing (also "type" column indicates well the size of the car)

Once the data was relatively well cleaned I split it into smaller datasets by type and continued cleaning the smaller datasets in new Jupyter Notebooks.

Individual Jupyter Notebooks for Each Car Type
After checking the distribution of the odometer data and since it wasn't symmetrical, I used median to replace NaN values.
Since each car type have very specific values for its type, I finely felt comfortable filling the missing values for each feature proportionately. 
Now there were no missing values. I also dropped the type feature since values were all the same.
I applied ordinal encoding to condition feature, all other non numerical features were treated with One Hot Encoding.
After creating histograms of price column and the logarithm of the price column to decide which one is more suitable for the machine learning model, I chose the logarithm for each ML model for each car type.

Selecting the best ML model.
Here are the steps I took for each car type:
split the data frame with a Logarithmic target: price,
Scaled the data with a StandardScaler to:
 * avoid bias towards features with   larger values
 * improve numerical stability:
 * reduce the impact of outliers
 * enable efficient use of resources
set a baseline to compare my models to,
created models with best parameters for:
 * Linear Regression with Polynomial 
Features 
 * Lasso Regression with Polynomial Features 
* Ridge Regression with Polynomial Features
Ran best models through SFS,
Ran best models through RFE*
Selected the best model with lowest testing MSE

Selecting features that influence the price of each car type.
After selecting the best ML model I ran that model through permutation Feature selection and got a list of the most influential features that affect the ML model.
To make the results more readable I created a chart of the features and their importance. 

Results
All results for each car type are listed in the pages below.

I also created a separate document for the "client" that is not familiar with the ML jargon. 
