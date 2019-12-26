create table supplier (supplierId number(3),sname varchar(20),Scity varchar(20) ,Sphone number(10),email varchar(20),primary key(supplierId));


create table Item (itemid number(3),itemname varchar(35), supplierId number(3),minqty number(3),maxqty number(4),price number(4),primary key(itemid),foreign key (supplierId) references supplier(supplierId));


create table orders (orderid number(4),orderdate date, custId number(4),quantity number(3) check(quantity>0), itemId number(3),primary key(orderid),foreign key (itemId)references item(itemId) );

create table customer (custid number(4) ,fname varchar(30),lname varchar(30),address varchar(50),phoneno number(11) not null,city varchar(20),country varchar(20),datefirstpurchased date,supplierid number(3),primary key(custid), foreign key (supplierid) references supplier(supplierid));


insert into supplier values(1,'dilip','chennai',8999900000,'dilip@abc.co.in');
insert into supplier values(2,'tarun','madurai',8999911111,'tarun@xyz.com');
insert into supplier values(3,'Naresh','Coimbatore',8999922222,'g.naresh@xyzl.com');
insert into supplier values(4,'Ganesan','Trichy',8999933333,'Ganesan_83@ijk.com');



insert into item values(20,'pears soap',4,7,20,30);
insert into item values(21,'V.V.D. coconut oil 400 ml',2,8,15,79);
insert into item values(22,'Ponds powder 400 g',3,6,25,106);
insert into item values(23,'Reynolds pen- blue',1,10,30,15);
insert into item values(24,'Reynolds pen- black',1,10,30,16);
insert into item values(25,'Mysore sandal soap',4,7,25,25);
insert into item values(26,'Fair and lovely cream- 50 g',3,5,15,55);
insert into item values(27,'Rexono deo spray',2,5,20,100);
insert into item values(28,'Dove soap',4,7,15,85);



insert into orders values(1,'12-jan-04',1001,30,25);
insert into orders values(2,'6-may-05',1202,38,24);
insert into orders values(3,'16-dec-06',1220,10,22);
insert into orders values(4,'21-may-04',1233,12,21);



insert into customer values(1001,'Das','Jeyaseelan','119,park avenue, IIstreet',9841093428,'coimbatore','India','10-jan-04',1);
insert into customer values(2001,'Gopi','govindraj','241,i floor,Kamaraj street ,Madippakam',9444124590,'Chennai','India','25-mar-05',4);
insert into customer values(1201,'Dilip','Kishore','43,II avenue,Anna Nagar',9997234534,'bangalore','India','20-aug-04',2);
insert into customer values(1300,'Aanand','chowdhury','43/1 sector 1, II street',9841054348,'bangalore','India','15-may-05',2);
insert into customer values(1220,'Chandra','Nagarajan','83,lal bagh',98410672356,'bangalore','India','12-feb-06',4);
insert into customer values(1221,'Abhishek','Kumar','13,kishori park',94447623901,'Chennai','India','15-may-04',1);
insert into customer values(1320,'nikhil','Pandit','218, alwaanya street',94448923091,'salem','India','21-apr-06',3);
insert into customer values(1222,'meenu','Monica','c11, church road',9841053421,'Tirchy','India','30-aug-04',1);
insert into customer values(1225,'pavan','kumar','128/A,north mada Street',99934782103,'maduari','India','18-aug-04',4);



select * from customer where city='Chennai' or city='chennai';
select * from customer where supplierid=2;
select custid,fname,lname from customer where datefirstpurchased>'31-jan-05';
select * from supplier where scity='Coimbatore';
select * from supplier where sname like 'G%';
select * from customer where lname not like '%e%';
select * from customer where datefirstpurchased >'31-dec-05' and datefirstpurchased <'01-jan-07' order by datefirstpurchased desc;
select * from orders where quantity<35;
select * from item where supplierid=4;
select * from item where supplierid=3 and minqty>7 order by itemid;