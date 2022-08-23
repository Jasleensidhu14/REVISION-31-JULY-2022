# REVISION-31-JULY-2022
FUNCTIONS AND SP 
/////////////////////////////REVISION 31 JULY 2022/////////////////////////////

use hurrysale 
select * from hurrysale 
//////USER DEFINED FUNCTIONS//////
DELIMITER &&
create function add_to_col3(a INT)
returns INT
DETERMINISTIC
BEGIN 
          declare b int ;
          set b = a+ 10;
          return b;
          end&&
          DELIMITER;
 /////////////////////////////////////////////////////////////////
select * from hurrysale 
select max(sales) from hurrysale
select add_to_col3(15) 
select * from hurrysale 
select quantity +10 from hurrysale 
select quantity, add_to_col3(quantity) from hurrysale 

DELIMITER &&
create function final_profit(profit int, discount int)
returns int
DETERMINISTIC
Begin 
Declare final_profit int ;
set final_profit  = profit - discount;
return final_profit;
end && 
select profit, discount, final_profit (profit, discount)from hurrysale; 
//////For decimal data type , write decimal(20,6) like this .It is an examplei.e. 20 before decimal on left side and 6 after decimal on right.//////
//////Make a udf to convert int datatype to string//////
DELIMITER &&
create function int_to_str(a INT)
returns varchar(50)
DETERMINISTIC
BEGIN 
          declare b varchar(50) ;
          set b = a;
          return b;
          end&&
   select int_to_str(33)      
   /////////////////////////////////
   select quantity, int_to_str (quantity) from hurrysale; 
   //////IF,IF...ELSE,IF ELSE IF USER DEFINED FUNCTIONS//////
   select quantity ,int_to_str(quantity) from hurrysale; 
   select max(sales) , min(sales) from hurrysale;
   select * from hurrysale
   /// Make a UDF for this product price range ///
   1 - 100 - super affordable
   100-300 - affordable
   300-600 - moderate 
	600+   - expensive ?

DELIMITER &&
create function mark_sales(sales int ) 
returns varchar(30)
DETERMINISTIC
begin 
declare flag_sales varchar(30); 
if sales  <= 100  then 
	set flag_sales = "super affordable product" ;
elseif sales > 100 and sales < 300 then 
	set flag_sales = "affordable" ;
elseif sales >300 and sales < 600 then 
	set flag_sales = "moderate price" ;
else 
	set flag_sales = "expensive" ;
end if ;
return flag_sales;
end &&
   
   select mark_sales(20) 
   select mark_sales(220) 
   select sales, mark_sales(sales) from hurrysale 
  //////LOOPS INSIDE MYSQL//////
