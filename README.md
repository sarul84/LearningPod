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

2. Create SOAP client in ASP.Net core

```
private MySoapClient GetSOAPClient()
{
    NetHttpsBinding binding = new NetHttpsBinding();
    binding.Security.Mode = BasicHttpsSecurityMode.Transport;
    binding.MessageEncoding = NetHttpMessageEncoding.Text;
    binding.MaxReceivedMessageSize = Int32.MaxValue;
    binding.MaxBufferSize = Int32.MaxValue;
    EndpointAddress ea = new EndpointAddress(<<ur URI>>);

    var client = new MySoapClient(binding, ea);
    return client;
}
```
3. Dynamics 365: What will happen if you set 0 to execution order in plugin step?

By default, the execution order for plugin is 1 and classic workflow execution order is 0 which means that the realtime workflows execute before any plugin step gets executed for the entity. If you would like to execute plugin before realtime workflow then set execution order to 0.

https://medium.com/@ras615/plugin-vs-workflow-execution-order-fa6b02c82b79

4. Dynamics 365: Difference between Append & AppendTo Access Level?

5. Dynamics 365: How many tables will be created in the back end if you create custom entity in MS CRM?


