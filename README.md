# EFCoreAndDapper-master

https://github.com/iammukeshm/EFCoreAndDapper

https://codewithmukesh.com/blog/using-entity-framework-core-and-dapper/


여기에 몇가지 수정한 부분이 있는데, asp.net mvc razor 사용이 가능하도록 한 부분과

services.AddControllersWithViews();
services.AddRazorPages();


app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();

    //endpoints.MapControllers();
});


아래 처럼 저장프로시저 가능하도록 하는 부분이 있음.

var addDepartmentQuery = $"Departments_Ins";

var p = new DynamicParameters();
p.Add("@Name", employeeDto.Department.Name);
p.Add("@Description", employeeDto.Department.Description);

var departmentId = await _writeDbConnection.QuerySingleAsync<int>(addDepartmentQuery, param: p, transaction: transaction, commandType: CommandType.StoredProcedure);
