
# How to Use Excel in C# Without Interop?
`IronXl` provides simplest way to use excel file in your C#  project without using Interop. it is very easy to communicate with excel file ,getting data from it and use it in your project.You can get rid of a lot of complicated lines of code and can use `IronXL` to get the easiest way.
## Access excel file in project: 
`WorkBook` is the class  `ironXL` whose object provides full eccess of excel file and its whole functions to the developers.for example if we want to access excel file,it is very easy as below:
```c# 
WorkBook wb = WorkBook.Load("sample.xlsx");//excel file path
```
in above code, `WorkBook.Load()` function load `sample.xlsx` in  `wb`. Any type function can be performed on `wb` by access specific sheet of excel file,by the following way we can access sheet of excel file.

## Access specific sheet from excel file:
To access the sheet in excel, `IronXL` provides `WorkSheet` class, it can be used by the following different ways:
```c#
WorkSheet ws = wb.GetWorkSheet("Sheet1"); //by sheet name
```
`wb` is WorkBook which decleared in above section.

OR
```c#
WorkSheet ws = wb.WorkSheets[0]; //by sheet index
```
OR


```c#
WorkSheet ws = wb.DefaultWorkSheet; //for the default sheet: 
```
OR

```c#
WorkSheet ws = wb.WorkSheets.First();//for the first sheet:
```
OR

```c#
WorkSheet ws = wb.WorkSheets.FirstOrDefault();//for the first or default sheet:
```
after getting excel sheet `ws` , you can get any type of data from corrosponding sheet of excel file and perform all excel function on it by the folloing way:
## Access Data from Sheet:
Data can be access from excel sheet `ws` in this way:

```c#
string c = ws["cell address"].ToString(); //for string
Int32 val = ws["cell address"].Int32Value; //for integer
```
it is also pssible to get data from many cells of specific column by the following way:
```c#
foreach (var cell in ws["A2:A10"])
{
    Console.WriteLine("value is: {0}",  cell.Text);
}
```
it will display values from cell `A2` to `A10`.

Code Example of above whole discussion is given below:
```c#
using IronXL;
WorkBook wb = WorkBook.Load("sample.xlsx");
WorkSheet ws = wb.GetWorkSheet("Sheet1");
foreach (var cell in ws["A2:A10"])
{
    Console.WriteLine("value is: {0}", cell.Text);
}
Console.ReadKey();

```
**It display the following result**

![output](https://github.com/ubaid4/ironxl/blob/master/doc3_input1.png)

**Screeshot of excel file `Sample.xlsx` is**

![output](https://github.com/ubaid4/ironxl/blob/master/doc3_1.png)

It can be observed that how much easy to use excel file data in our project without using Interop.
## Perform Functions on Data:
it is very easy to access filtered data from excel sheet by applying aggregate functions like Sum,Min or Max by the following way:
```c#
decimal sum = ws["From:To"].Sum();
decimal min = ws["From:To"].Min();
decimal max = ws["From:To"].Max();
```
Exapmle code above discussion:

```c#
using IronXL;
WorkBook wb = WorkBook.Load("sample.xlsx");
WorkSheet ws = wb.GetWorkSheet("Sheet1");

decimal sum = ws["G2:G10"].Sum();
decimal min = ws["G2:G10"].Min();
decimal max = ws["G2:G10"].Max();

Console.WriteLine("Sum is: {0}", sum);
Console.WriteLine("Min is: {0}", min);
Console.WriteLine("Max is: {0}", max);
Console.ReadKey();

```
**It display the following result**

![output](https://github.com/ubaid4/ironxl/blob/master/doc3_output2.png)

**Screeshot of excel file `Sample.xlsx` is**
![output](https://github.com/ubaid4/ironxl/blob/master/doc3_2.png)




