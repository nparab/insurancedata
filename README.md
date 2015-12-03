



Data Analysis in Insurance Industry
-----------------------------------



-----------------------------------

In this Project, We have analyzed an insurance industry data for car Accidents.To analyze the data follow the steps.

**Prerequisites:**

Microsoft Azure account [Click here for trial account][1]

Cloud Berry for Azure [To download click here][2]


**Steps:**


 
  

 **1.** After creating an account on
    Microsoft's Azure, create
    an HDInsight cluster.





 - Go to Azure portal after creating an account in Azure.


 - Click on New

 - In Data+Analytics, Select HDInsight

 - A new pop-up will appear, Type the cluster name.
Select type as "Hadoop", Operating  System as"Linux", Select Total node as 2, Put Login name and password, And click on *create*.

 - Azure will start deploying a cluster. It will take few minutes to complete the  process.

 

**2.**  After Creating the cluster, we  will upload data into the cluster. You can get Insurance's Sample data in "DATASET". 

**3.**  To upload data in the cluster we will use Cloudberry for Azure.

 - Open the Cloudberry, once it is installed on local machine.
 - Select Azure Blob In the dialog box, add the details as mentioned while creating cluster and upload file to the cluster.



**4.** After uploading the data, Go to the Azure where the cluster is created.




**5.** In Hive, First thing is to create table.

 - For, Creating the table run this query in a query editor. 

  

     <pre>CREATE TABLE INSURANCE_DATA
(policy_number int,household_id int,vehcile int ,
registered_till int,claimed_year int,
state string,car_model string,claim_amount int)
ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' 
TBLPROPERTIES("skip.header.line.count"="1"); </pre>

 - After the table is created, add data to the table by the following query.
 
 <pre>LOAD DATA INPATH '\HdiSamples\InsuranceData.csv' 
OVERWRITE INTO TABLE INSURANCE_DATA;</pre>


 - Now data is ready to analyse.


**6.** Now, Analyse the data  using following queries.

 -  Number of claims for  each the years

  <pre>select claimed_year,count(*) from INSURANCE_DATA group by claimed_year;</pre>


 - Number of claims for each state.
  <pre>select state,count(*) from INSURANCE_DATA group by state;</pre>




 - Total Claimed amounts for each state. 

 <pre>select state,sum(claim_amount) from INSURANCE_DATA group by state;
</pre>



 - Numbers of car models met with accident each year.

 <pre>Select car_model,count(*) from INSURANCE_DATA group by car_model;</pre>



**7.** After data is analysed in Hive, go to Microsoft excel.

 - Select Data tab on top.

 - From Other Sources.

 - From Microsoft Query.

 - Hive

 - Add the columns

 - Next, and finish.

 - In Insert tab, Select power query.

  - Project the data.

   

    

 


          
 

 


  [1]: https://azure.microsoft.com/en-us/pricing/free-trial/?WT.srch=1&WT.mc_ID=SEM_ZHl3YJWF
  [2]: http://www.cloudberrylab.com/download-thanks.aspx?prod=cbazure