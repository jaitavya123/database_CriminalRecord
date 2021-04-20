# database_CriminalRecord
MySql database for Criminal Record project
use sys

/* First Table   */
create table Criminal_info(id varchar(12) primary key , Name varchar(50) unique key, Father varchar(50), Mother varchar(50) , Address_Proof varchar(3000))
insert into Criminal_info values('RJ2020_1','Sunil Jain', 'Paras Jain ', 'Randi Jain ', ' Ganesh Villa PG Foils Colony Pipalia Kalan(306307)') 
select* from Criminal_info
insert into Criminal_info values('RJ2010_4','Kuldeep A.K.A Doctor','Vishnu ', 'Pani devi ','Hansi,Haryana' ),('RJ2020_5','Sonu Gujar (Leader of SonunGujar Gang )','Badal Gujar','Omi devi Gujar','Beri, Jaipur') 
update Criminal_info set Pic=load_file('C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/lb.jpg') where id='RJ2020_2';
update Criminal_info set Pic=load_file('C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/sonu.jpg') where id='RJ2020_5';

alter table Criminal_info rename column id to C_id;
/* Second Table   */
create table Criminal_Physique (id varchar(12) unique key, Height float(3,2),Weight int(3),Birth_Date date)
insert into Criminal_Physique values('RJ2020_1',5.6,34,'1987-07-21')
select*from Criminal_Physique
drop table Criminal_Physique
insert into Criminal_Physique values('RJ2020_2',5.6,34,'1981-02-01')
delete from Criminal_Physique where id='RJ2010_5'
alter table Criminal_Physique rename column id to C_id;

select * from  Criminal_info i join Criminal_Physique p on i.id=p.id
/* Third Table   */
create table Case_History (caseID int unique key,courtID varchar(7) not null,c_id varchar(12),FIR_Sr int, case_status varchar(10) );

insert into Case_History value(456789,'RJJD857','RJ2009_5',9876,'Dismissed');
insert into Case_History value(78954,'RJJP347','RJ2020_1',7856,'Dismissed');
insert into Case_History value(495678,'RJDU234','RJ2020_2',8967,'Dismissed');
insert into Case_History value(56578,'RJUD789','RJ2020_3',9678,'Dismissed');
insert into Case_History value(48763,'RJAJ589','RJ2020_4',7569,'Dismissed');
select*from Case_History

/* Fourth Table  */
create table Judicial_Reord(caseID int(12) not null,courtID varchar(7) not null);
insert into Judicial_Reord value(48763,'RJAJ589');
insert into Judicial_Reord value(78954,'RJJP347');
insert into Judicial_Reord value(495678,'RJDU234');
insert into Judicial_Reord value(56578,'RJUD789');
insert into Judicial_Reord value(48763,'RJAJ589');

select*from Judicial_Reord;

/* Fifth Table  */
create table Court_detail(courtID varchar(7) not null,location varchar(7) not null);

insert into  Court_detail value('RJAJ589','Ajmer');
insert into  Court_detail value('RJJP347','Jaipur');
insert into   Court_detail value('RJDU234','Dehradun');
insert into  Court_detail value('RJUD789','Udaipuur');
insert into  Court_detail value('RJAJ589','Ajmer');
alter table Court_detail modify location varchar(7) into location varchar(34) ; 

select*from Court_detail;
/* Combine 3 tables using JOIN  */
select*from Criminal_info i join Criminal_Physique p on i.id=p.id join Case_History r on p.id=r.id join a on a.id=r.id
