# LearningPod

1. Write a query to get organization hierarchy based on employee id

Table creation: 

```
CREATE TABLE [dbo].[Emptable](
	[Id] [bigint] IDENTITY(30000,1) NOT NULL,
	[EmpName] [varchar](100) NULL,
	[ManagerId] [bigint] NULL,
	[Designation] [varchar](100) NULL
) ON [PRIMARY]
```
Select Query:

```
declare @id bigint 
set @id = 30003;
with cte As
(
	select Id, EmpName, ManagerId,Designation from [dbo].[Emptable] where id = @id
	union all 
	select a.Id, a.EmpName, a.ManagerId,a.Designation from [dbo].[Emptable] a 
	inner join cte c 
	on c.ManagerId = a.id 
	 
)
select * from cte 
```
