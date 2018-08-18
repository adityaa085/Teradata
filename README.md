Write DML queries for the following questions

    1.	Display unique Jobs from EMP table
    select distinct job from emp
    
    2.	List the employees in the ascending order of their salaries
    select ename,sal from emp order by sal asc
    
    3.	List the details of the employees in ascending order of the dept no and descending of Jobs
    select ename,deptno,job from emp order by  deptno asc,job desc
    
    4.	Display all the unique job groups in the descending order
    select distinct job from emp order by job desc
    
    5.	Display all the employees who are managers
    select ename,empno,job from emp where job='manager'
    
    6.	List the employees who joined before 1981
    select ename,hiredate from emp where hiredate < '1981-01-01'
    
    7.	List the Empno, Ename, Sal, daily sal of all employees in the ascending order of annual sal
    select ename,empno,sal,(sal/(12*30)) as "daily salary" from emp order by sal asc
    
    8.	Display the Empno, Ename, job, Hiredate, Exp of all Mgrs
    select ename,empno,job,hiredate,(current_date-hiredate)/365.25 as "exp" from emp where job='manager'
    
    9.	List the Empno, Ename, Sal, experience of all employees working for Mgr=7369
    select ename,empno,job,hiredate,(current_date-hiredate)/365.25 as "exp",mgr from emp where ename in (select e.ename from emp e where e.mgr=7369)
    
    10.	Display all the details of the employees whose Comm. Is more than their Sal
    select ename,sal,comm from emp where comm > sal
    
    11.	List the employees in the asc order of Designations of those joined after the second half of 1981
    select ename,hiredate,job from emp where hiredate>'1981-06-30' order  by job
    
    12.	List the employees along with their experience and daily salary is more than Rs.100
    elect ename,(current_date-hiredate)/365.25 as expri, (sal/(12*30)) as "daily sal" from emp where "daily sal">100
    
    13.	List the employees who are either ‘CLERK’ or ‘ANALYST’ in the Desc order
    select ename,job from emp where job='analyst' or job = 'clerk'
    order by ename desc 
    
    14.	List the employees who joined on 1-MAY-81,3-DEC-81,17-DEC-81,19-JAN-80 in asc order of seniority
    select ename,hiredate from emp 
    where hiredate in ('1981-05-01','1981-12-03','1981-12-17','1980-01-19')
    order by hiredate asc
    
    15.	List the emp who are working for the Deptno 10 or20
    select ename,deptno from emp where deptno=10 or deptno=20
    
    16.	List the employees who are joined in the year ‘81
    select ename,hiredate from emp where hiredate between '1981-01-01' and '1981-12-31'
    
    17.	List the employees who are joined in the month of Aug 1980
    select ename,hiredate from emp where hiredate between '1980-08-01' and '1980-08-31'
    
    18.	List the Enames those are having five characters in their Names
    select ename from emp where ename like '_____'
    
    19.	List the Enames those are starting with ‘S’ and with five characters
    select ename from emp where ename like 's____'
    
    20.	List the employees those are having four chars and third character must be ‘r’
    select ename from emp where ename like '__r_'
    
    21.	List the Five character names starting with ‘S’ and ending with ‘H’
    select ename from emp where ename like 's___h'
    
    22.	List the employees whose Sal is four digit number ending with Zero
    select ename,sal from emp where (sal between 1000 and 9999 )and (sal/10 between 100 and 999)
    
    23.	List the employees whose names having a character set ‘LL’ together
    select ename from emp where ename like  any ( '%ll%' , 'll%' , '%ll')
    
    24.	Display the Empno, Ename, Sal, Dname, Loc, Deptno, Job of all employees working at CJICAGO or working for ACCOUNTING dept with Ann Sal>28000, but the Sal should not be=3000 or 2800 who doesn’t belongs to the Mgr and whose no is having a digit ‘7’ or ‘8’ in 3rd position in the asc order of Deptno and desc order of job
    
    select distinct e.ename,e.empno,e.sal,d.dname,d.loc,e.deptno,e.job from emp e  inner join dept d on e.deptno=d.deptno 
    where d.loc='chicago' or (e.job='accounting' and e.sal>28000 )and(e.mgr<>emp.empno and e.sal not in (3000,2800))and (cast(e.empno as varchar(10))  like any('__7%','__8%'))
    order by e.deptno desc,e.job asc
    
    25.	List the Empno, Ename, Sal, Dname,Exp, and Ann Sal of employees working for Dept10 or20
    select e.ename,e.empno,e.sal,d.deptno,d.dname,(current_date -e.hiredate )/365.25 as experience from emp e
    inner join dept d on d.deptno=e.deptno where e.deptno in (10,20)
    
    26.	List the details of the employees whose Salaries more than the employee BLAKE
    select ename,sal from emp where sal>(select sal from emp where ename='blake')
    
    27.	List the employees whose Jobs are same as ALLEN
    select ename,job from emp where job=(select job from emp where ename='allen')
    
    28.	List the employees who are senior to King
    select ename from emp where empno=(select mgr from emp where ename='king')
    
    29.	List the Employees who are senior to their own MGRS
    30.	List the Employees of Deptno 20 whose Jobs are same as Deptno10
    select ename,deptno,job from emp where deptno=20 and job in(select job from emp where deptno=10)
    
    31.	List the Employees whose Sal is same as FORD or SMITH in desc order of Sal
    select ename,sal from emp where sal in (select sal from emp where ename='smith' or ename='ford')
    order by sal desc 
    
    32.	List the employees Whose Jobs are same as MILLER or Sal is more than ALLEN
    select ename,job,sal from emp where job=(select job from emp where job='miller') or
    sal>(select sal from emp where ename='allen')
    
    33.	List the Employees whose Sal is > the total remuneration of the SALESMAN
    select ename,sal from emp where sal>(select sum(sal) from emp where job='salesman')
    
    34.	List the employees who are senior to BLAKE working at CHICAGO & BOSTON
    35.	List the employee names and his average salary department wise
    select deptno,avg(sal) from emp
    group by deptno
    
    36.	Find out least 5 earners of the company
    select ename,rank(sal asc),sal from emp 
    qualify rank(sal)>11
    order by sal 
    
    37.	Find out employees whose salaries greater than salaries of their managers
    select e.ename,e.sal,m.sal as"manager salary" from emp e,emp m where e.mgr=m.empno and m.sal <e.sal
    
    38.	List the managers who are not working under the president (the manager should not be president)
    select e.ename,e.job,m.job,e.empno,e.mgr  from emp e,emp m where e.mgr=m.empno and m.job<>'president'
    
    39.	List the records from emp whose deptno isnot in dept table
    select deptno,dname from dept where deptno not in(select deptno from emp )
    
    40.	List the details of the employees in the ascending order of the sal
    select * from emp 
    order by sal asc 
    
    41.	List the dept in the ascending order of the job and the desc order of the employees print empno, ename
    select e.ename,e.empno, d.dname from emp e inner join dept d on e.deptno=d.deptno 
    order by  job asc,ename desc  
    
    42.	Display the unique dept of the employees as in employee table
    select distinct e.deptno,d.dname from emp e inner join dept d on e.deptno=d.deptno 
    
    43.	Display the details of the BLAKE
    select * from emp where ename='blake'
    
    44.	List the emp whose annual sal is <25000 in the asc order of the salaries
    select * from emp where sal<25000
    order by sal asc 
    
    45.	List the empno,ename,sal,TA30%,DA 40%,HRA 50%,GROSS,LIC,PF,net,deduction,net allow and net sal in the ascending order of the net salary
    46.	List all the 4char employees
    select ename from emp
    where ename like '____'
    
    47.	List the employees whose sal is ending with 00
    select ename,sal from emp where cast(sal as varchar(10))  like '%00.'
    
    48.	List employees who joined in the month having second char ‘a’
    select ename, cast((hiredate( format 'mmm'))as char(3)) as mon from emp where mon like '_a%'
    
    49.	List the emp who are clerks who have exp more than 8yrs
    select ename,job,hiredate from emp where job='clerk' and (current_date -hiredate )/365.25>8
    
    50.	List the employees joined in jan with salary ranging from 1500 to 4000
    select ename,hiredate,sal from emp where (extract(month from hiredate )=01) and sal between 1500 and 4000
    
    51.	List the employees along with exp of those working under the mgr whose number is starting with 7 but should not have a 9 joined before 1983
    select ename,mgr,(current_date-hiredate)/365.25 as expri from emp where (cast(mgr as varchar(10)) like '7%') and (cast(mgr as varchar(10))  not like all('%9','9%','%9%')) and (hiredate <'1983-01-01')
    
    52.	List the employees who are working as either mgr or analyst with the salary ranging from 2000 to 5000 and without commission
    select distinct e.ename from emp e,emp m where e.mgr=m.empno or e.job='analyst' and e.sal between 2000 and 5000 and e.comm is null
    
    53.	List the empno,ename,sal,job of the employees with /annsal<34000 but receiving some comm.
      Which should not be>sal and designation should be sales man working for dept 30
    select ename,empno,sal,job,comm from emp where sal<34000 and comm is not null  and 
    comm>sal and job='salesman' and deptno=30 
    
    54.	List the empno,ename,sal,job,deptno&exp of all the employees belongs to dept 10 or 20 with an exp 6 to 10 y working under the same mgrwith out comm. With a job not ending irrespective of the position with comm.>200 with exp>=7y and sal<2500 but not belongs to the month sep or novworkingunder the mgr whose no is not having digits either 9 or 0 in the ascdept&descdept
    55.	List the details of the employees working at Chicago
    select e.ename,e.empno,d.deptno,d.loc  from emp e inner join dept d  on e.deptno=d.deptno where d.loc='chicago'
    
    56.	List the empno, ename, sal, loc of the employees working at Chicago dallas with an exp>6ys
    select e.ename,e.empno,d.deptno,d.loc,e.hiredate  from emp e inner join dept d  on e.deptno=d.deptno where d.loc='chicago' or d.loc='dallas' and (current_date -e.hiredate )/365.25 >6
    
    57.	List the employees along with loc of those who belongs to dallas ,newyork with sal ranging from 2000 to 5000 joined in 81
    select e.ename,e.empno,d.deptno,d.loc,e.hiredate  from emp e inner join dept d  on e.deptno=d.deptno where d.loc='newyork' or  d.loc='dallas' and sal between 2000 and 5000 and extract(year from hiredate)=1981
    
    58.	List the employees who are senior to MILLER
    59.	List the total salary, maximum and minimum salary and average salary of the employees deptnowise, for department 20 and display only those rows having an average salary > 1000
    select deptno,max(sal),min(sal),avg(sal),sum(sal) from emp 
    group by deptno having avg(sal)>1000
    
    60.	Display the name and employee number of the employee who is earning the second highest salary
    select ename,empno,sal from emp qualify rank(sal)=2
    
    61.	List the department number and total salary payable in each department
    select deptno,sum(sal) from emp 
    group by deptno 
    62.	List names of employees who are more than 2 years old in the company
    select ename,hiredate  from emp where (current_date-hiredate)/365.25 >2
    
    63.	List the maximum salary paid to a salesman
    select ename,job,sal from emp
    where job='salesman' and sal=(select max(sal) from emp where job='salesman')
    
    64.	List the name of the employee and designation of the employee who does not report to anybody
    select ename,job from emp 
    where mgr is null
    
    65.	List the total salary, maximum and minimum salary and average salary of the employees, for department 20.
    select max(sal),min(sal),avg(sal),sum(sal),deptno from emp
    group by deptno
    having deptno=20
    
    66.	List employees whose job is same as that of Smith
    select ename,job from emp 
    where job=(select job from emp where ename='smith')
    
    67.	List employee getting the max salary
    select ename,deptno,job from emp
    where sal=(select max(sal) from emp)
    
    68.	List all managers
    select distinct m.ename as "manager's name"  from emp e,emp m where e.mgr=m.empno
    
    69.	List employees who are not managers
    70.	List all employees who earn more than the average salary in their department
    select e.ename,e.sal from emp e
    where sal > (select avg(sal) from emp group by deptno having emp.deptno=e.deptno)
    
    71.	List employees whose salary is greater than their manager’s salary
    select e.ename,e.sal from emp e,emp m where e.mgr=m.empno and e.sal>m.sal
    
    72.	List employees who work in Research department
    select e.ename,d.dname from emp e inner join dept d on d.deptno=e.deptno where d.dname='research'
    
    73.	List name, salary and PF amount of all employees. (PF is calculated as 10% of basic salary)
    select ename,sal, (sal*10/100) as pf from emp
    
    74.	List the employee names of analysts and salesmen.
    select ename,job from emp where job='analyst' or job='salesman'
    
    75.	List the names of those employees whose employee numbers are 7369, 7521, 7839, 7934, 7788.
    select ename,empno from emp where empno in(7369,7521,7839,7934,7788)
    
    76.	List those employees who do not belonging to department 30, 40, or 10.
    select ename,deptno from emp where deptno not in(10,30,40)
    
    77.	List those employee names who have joined between 30 June and 31 Dec ‘81.
    select ename,hiredate from emp where hiredate between '1981-06-30' and '1981-12-31'
    
    78.	List the different designations available in the company
    select distinct job from emp 
    
    79.	List those employees name that are not eligible for commission
    select ename,comm from emp where comm is null
    
    80.	List the name of the employee and designation of the employee who does not report to anybody
    select ename,empno,job from emp where mgr is null
    
    81.	List the employees who are eligible for commission
    select ename,comm from emp where comm is not null 
    
    82.	List names of employees if the names have “i” as the second character
    select ename from emp where ename like '_i%'
    
    83.	Display the names of all employees with their salary and commission earned. Employees with a null commission field should have 0 in the commission column
    select ename,sal,comm from empnow 
    


3.2	Round 2 – Group by clause
Write queries for the following questions


    1.	List the count and average salary for employees in department 20.
        
         Select avg(sal),count(sal)from group by deptno having deptno=20;
    
    2.	List names of employees who are older than 30 years in the company. 
    
         select ename from emp where (current_date-hiredate)/365.25 <30;
    
    
    3.	List the employee name , hire date in the descending order of the hire date
    
         select ename,hiredate from emp order by hiredate desc
    
    4.	List employee name, salary, PF, HRA, DA and gross; order the results in the ascending order of gross.
            HRA is 50% of the salary and DA is 30% of the salary.
    
          select ename,sal,sal*0.20 as PF,sal*0.50 as HRA,sal*0.30 as DRA,(sal+pf+hra+dra) as gross
     from emp  order by gross asc
    
    5.	List the department numbers and number of employees in each department
    
         select deptno,count(empno) from emp group by deptno;
    
    6.	List the department number and total salary payable in each department.
    
         select deptno,sum(sal) from emp group by deptno;
    
    7.	List the jobs and number of employees in each job.
            The result should be in the descending order of the number of employees
    
         select job,count(empno) from emp group by job order by count(empno) desc;
    
    8.	List the total salary, maximum and minimum salary and average salary of the employees jobwise
    
         select job,count(empno),sum(sal),min(sal),max(sal),avg(sal) from emp group by job
    
    9.	List the total salary, maximum and minimum salary and average salary of the employees, for department 20.
       
         select  sum(sal),min(sal),max(sal),avg(sal) from emp where deptno=20;
    
    10.	List the average salary of the employees job wise, for department 20 and
            display only those rows having an average salary > 1000
    
    
       select avg(sal) as avgsal,job from emp where deptno=20 group by job having avg(sal)>1000

3.3	Round 3 – SUBQUERIES
Write queries for the following questions

    1.	List employees whose job is same as that of Smith 
    
        select ename,job from emp where job=(select job from emp where ename='SMITH');
    
    2.	List employees who have joined after Adam 
    
        select ename,hiredate from emp where hiredate>(select hiredate from emp where ename='ADAMS');
    
    3.	List employees who salary us greater than Scott’s salary 
    
        select ename,sal from emp where sal>(select sal from emp where ename='SCOTT');
    
    4.	List employees getting the max salary 
    
       select * from emp where sal=(select max(sal) from emp);
    
    5.	List employees show salary is > the max salary in deptno 30 
    
       select sal,ename from emp where sal>(select max(sal) from emp where deptno=30);
    
    6.     List all employees whose department and designation is same as that of employee with empno 7788
    
      select * from emp where (deptno,job)=(select deptno,job from emp where empno='7788' );
    
    7.	List employee who are not managers 
     
      select *from emp where empno not in(select  distinct mgr from emp where mgr is not null)
    
    8.	List all managers 
    
      select *from emp where empno in(select mgr from emp)
    
    9.	List all employees who earn more than the average salary in their department 
    
      select e.deptno,sal,ename,avgsal from emp e join (select deptno,avg(sal) avgsal from emp group by deptno)
       as d on e.deptno=d.deptno
       where sal > (select avg(sal) from emp ie where ie.deptno=e.deptno) order by d.deptno ;
    
    (or) 
        select ename,empno,sal,deptno from emp e where sal>(select avg(sal) from emp m group by deptno
     having m.deptno=e.deptno)
    
    10.	List employees whose salary is greater than their manager’s salary 
    
        select e.empno as EMPNO,e.sal as EMPSAL,
        m.empno as MGRNO,m.sal  as MGRSAL from emp e join emp m on e.mgr=m.empno
        where e.sal>m.sal
    
    11.	List departments with no employees
    
        select e.empno,d.dname,d.deptno from emp e full outer join dept  d
        on e.deptno=d.deptno where empno is null
	


3.4	Round 4 – Joins (Mortal mode)

    1.	List employee name, department number and their corresponding department name
    
      select e.ename,d.deptno,d.dname from emp e join dept d on e.deptno=d.deptno;
    
    2.	List employee name and their manager name 
    
      select e.ename,m.ename as "Manager Name" from emp e join emp m on e.mgr=m.empno;
    
    3.	List employees who work in Research department 
      
      select * from emp e join dept d on e.deptno=d.deptno where d.dname='RESEARCH';
    
    4.	List all rows from EMP table and only the matching rows from DEPT table
    
      select * from emp e left outer join dept d on e.deptno=d.deptno;
    
    5.	List all rows from EMP table and only the matching rows from DEPT table
    
      select * from emp e left outer join dept d on e.deptno=d.deptno;
    
    6.	Write a query to perform full outer join between EMP and DEPT tables 
    
      select * from emp e full outer join dept d on e.deptno=d.deptno where empno is null;
    
    7.	List employee name, their manager name and managers manager name
    
      select e.ename,m.ename as "Manager Name",d.ename as "Managers Manager"
      from emp e, emp m ,emp d where e.mgr=m.empno and m.mgr=d.empno




3.5	Round 5 – Tables& Data types:

    1.	Create table sample1 with 1 column and insert 5 records of your own
    
        create table sample1(empno integer);
        insert into sample1 values(10);
        insert into sample1 values(20);
        insert into sample1 values(30);
        insert into sample1 values(40);
        insert into sample1 values(50);
        
    
    2.	Insert existing record which have been inserted already and verify
    
    
       Statement 1: INSERT Failed. 2802:  Duplicate row error in Samples.sample1.
    
    3.	Create new table with 1 column which can allow duplicate records.
    
      create mutliset table sample2 (sal integer );
    
    4.	Create new table empcopyand copy all records of emp 
     
      create table empcopy as emp with data;
    
    5.	Create new tabledeptcopy and copy only the schema of depttable
    
      create table tabledeptcopy as dept with no data;
    
    6.	Create new table empdeptand copy records from emp and dept tables
    
      create table empdept as emp with data;
  
3.6	Round 6 – Constraints:

    1.	Create a new tabletemp06 with 1 column and the user should not be able to insert NULL.
    
       create table tabletemp_06 (empno integer not null);
    
    2.	Create new table with temp07 with 1 column and the system should allow
            only the unique values to be inserted.(PK)
    
       create table temp07(empno integer primary key not null);
    
    3.	Create new table temp_piwith 2 columns with primary index for the 2nd column.
    
       create table temp( sal integer not null, empno integer primary key not null);
    
    4.	Create new table temp_fkwith Foreign Key constraint
    
        create table tempfk_with( sal integer not null,
         empno integer primary key not null,mgr integer references  tempfk_with(empno));
    
    5.	Create new table temp_pk2 with primary key for more than 1 column.
    
         create table temp_pk(
          empno integer not null,
          ename varchar(20) not  null,
          deptno integer not null,
          primary key(empno,deptno)
          )
    
    6.	Create new table temp_uk2 with unique key for more than 1 column.
    
    
          create table temp_uk(
          empno integer unique not null,
          ename varchar(20) not  null,
          deptno integer not null,
          adid integer unique not null
          )
    
    7.	Create new table temp_cc and it contains column age. The user should be able enter age between 18 and 55.
    
          create table temp_cc(
          age integer constraint age_check check (age>18 and age <55))
    
    8.	Update the sample table with UPSERT process.
    
          update emp set sal=4500 where empno=7788 else
          insert into emp(empno,ename,sal) values(7788,'scott',4500);


3.7	Round 7 – Views:

     1.	Create a view temp_view with all records of emp table.
          create view temp_view as select * from emp 
          select * from temp_view
    
    
         2.	Insert a new row in the view temp_view.
          insert into temp_view(empno,ename,job,mgr,hiredate,sal,comm,deptno) 
          values(9999,'RAJAJI','ANALYST',7783,'1981-05-05',5000,null,10);
    
    
         3.	Update  existing record in the view temp_view.
          update temp_view set empno=1111 where ename='SCOTT'
          select * from temp_view
    
         4.	Create new view temp_join with combination of 2 tables.(emp and dept tables).
         create view temp_join (empno,ename,job,mgr,hiredate,sal,comm,deptno) as 
         select  e.empno,e.ename,e.job,e.mgr,e.hiredate,e.sal,e.comm,e.deptno from emp e inner join dept d on(e.deptno=d.deptno)
         select * from temp_join
    
    
         5.	Create new view temp_where with constraint of deptno is 10.
         create view temp_new as select * from emp where deptno=10;
         select * from temp_new
    
    
    
         6.	Add a new row into the view temp_wherewith deptno 20.
         insert into temp_new(empno,ename,job,mgr,hiredate,sal,comm,deptno) 
         values (9999,'RAJAJI','ANALYST',7783,'1981-05-05',5000,null,10)  
    
    
         7.	Create new view with ‘with check option’.
         create view temp_view1 as select * from emp with check option;
         insert into temp_view1(empno,ename,job,mgr,hiredate,sal,comm,deptno) 
          values(9999,'RAJAJI','ANALYST',7783,'1981-05-05',5000,null,10); 
         select * from temp_view 
 
3.8	Round 8 – Macros:
         1.	Create new macro mac01 and it should list all the empno fromemptable.
         create macro mac01 as(select empno from emp;)
         exec mac01 ;
    
    
    
         2.	Create new macro that should display all records from emp and dept tables one by one.
         create macro m02 as(select * from emp;select * from dept;)
         exec m02 ;
    
         3.	Create new macro mac02with 3 columnsand should accept inputs during run time(on execution).
         create macro mac03(a integer,b integer,c integer) as (select :a,:b,:c)
         exec mac03(5,6,7)






3.9	Round 9 – Analytical Functions:


    1.	List deptno,job,totalsal from emptable using ROLLUP function.
    
        select deptno,job, sum(sal) as salary from emp
        group by rollup(deptno,job)
        order by 1,2
    
    
    2.	List deptno,job, total sal from emptable using CUBE function
    
      select deptno,job, sum(sal) as salary from emp
      group by cube(deptno,job)
      order by 1,2
    
    3.	List ename,job,sal from emptable using CSUM function
    
    
      select ename,job,sal,csum(sal,deptno) from emp;
    
    4.	List empno,sal,deptno,mavg from emptable using MAVG function.
    
      select empno,job,sal,deptno,mavg(sal,2,empno) as movavg from emp
    
    5.	List empno,deptno,msum from emptable using MSUM function.
    
     select empno,job,sal,deptno,msum(sal,2,empno) as movsum from emp
    
    
    6.	List empno,sal,mdiff from emp table using DIF function
    
     select empno,sal,deptno,mdiff(sal,2,empno) as movdif from emp;
    
    7.	List all the records from emptable and show the rank according to salary.
    
     select empno,ename,sal,rank(sal) from emp

  







3.10	Round 10 – Import & Export:
Create WebEx record for the below tasks:

         1.	Create a new SQL file which should be exported in DATA format.
    
            .logon localtd/tduser
            .export data file='c:\newname.txt'
            select * from samples.emp where ename='SCOTT';
            .export reset;
            .logoff;
    
    
             bteq
            login localtd
             tduser
    
    
             .run file='c:\exp1.txt'
    
            
    
         2.	Create new SQL file which should be exported in REPORT format( export first 10 records only)
           .logon localtd/tduser;
           .export report file='c:\nemname.txt';
           select * from samples.emp;
           .export reset;
           .logoff;
    
           bteq
           login localtd
            tduser
           .run file 'c:\ext1.txt'
    
        
    
    
    
         3.	Create new SQL file which should be exported in CSV format.
           .logon localtd/tduser;
           .export dif file='c:\newname.csv';
           select * from samples.emp;
           .export reset;
           .logoff;
    
    
           bteq
           login localtd
           tduser
           .run file 'c:\ext1.txt'
    
    
         
    
         4.	Create new SQL file which should be exported in xls format.
          .logon localtd/tduser;
          .export indicdata file='c:\abc.txt';
          select * from emp;
          .export reset;
          .logoff; 
    
    
           bteq
           login localtd
           tduser
           .run file 'c:\ext1.txt'
    
    
    
    
         5.	Create new SQL file which should import data from txt file and should get inserted 
            into the newly created table in BTEQ Database.
           
            .logon localtd/tduser;
            .import data file='c:\abc.txt';
            .repeat *
            using 
            eid integer,
            ename varchar(10)
            insert into samples.abc values(:eid,:ename);
            .logoff;
