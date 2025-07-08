# Transformation

At this stage, I created Notebook in Fabric to clean and transform the data from the Bronze layer into more structured Silver tables, and then enriched those into Gold tables using PySpark. While doing this, I also thought ahead about how the data would be used, so I shaped the Gold tables to support the kind of analysis and reporting we’ll need later.


## Transform bronze to silver table
To start, I reviewed the schema and identified the key tables needed to meet the business requirements for the procurement and  these include:

- *Purchasing.OrderDetail*
- *Purchasing.OrderHeader*
- *Production.Product*
- *Purchasing.Vendor*
- *Production.ProductCategory*
- *Production.ProductSubCategory*
  
This process involved basic transformation of the date fields to readable formats which we would make use of later on.

[Bronze-to-Silver Notebook]()


## Transform silver to gold

At the gold level I would have facts and dimension tables which would be used for the sematic model. 

   **Dimention Tables**
- dim_date
- gold_dim_product
- gold_dim_product_category
- gold_dim_vendor
- gold_dim_orderheader
- gold_dim_vendorleadtime
  
**Fact Table**
-  gold_fact_procurement

[Silver-to-Gold Notebook]()
