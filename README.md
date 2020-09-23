<div align="center">

## VB for JavaScript


</div>

### Description

Updated 11/19/2004

Added check for deliminator (/ - or .)

This JavaScript file allows coders to use common VB functions that are not available in JavaScript to handle strings and dates, functions include Parse(), Len(), Left(), Right(), inStr(), DateAdd() and DateDiff().
 
### More Info
 
Inputs for all functions are the same as in VB, the data type and quantity are the same.

use is explained in the top of the file, the file is a .txt extention for download just chaneg the extention to .js to use it

the functions return a variable of the same name as the function

none that I know of

2/16/05

Fixed bug for months with 31 days.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Steve Palmer](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/steve-palmer.md)
**Level**          |Advanced
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB 6\.0, ASP \(Active Server Pages\) 
**Category**       |[Internet/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-html__1-34.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/steve-palmer-vb-for-javascript__1-57293/archive/master.zip)





### Source Code

```
/*
these are common VB functions tyhat are not available in javascript
just include a refferance to the VB.js file in you header file.
script type="text/javascript" language="JavaScript" src="vb.js"
*/
//return the length of a string
function Len(string){
	var Len = string.length;
	return Len;
}
//return a number of characters from the right side of a string
function Right(string,count){
	var Start = Number(string.length) - Number(count);
	var End = Number(string.length);
	var Right = string.substring(Start,End);
	return Right;
}
//return a number of characters from the left side of a string
function Left(string,count){
	var End = Number(count);
	var Left = string.substring(0,End);
	return Left;
}
//return an array of string bits from a string
function Parse(string,deliminator){
	var Parse = string.split(deliminator);
	return Parse;
}
//find an instance of a characters in a string and return the integer possition
function inStr(start,string1,string2){
	if(start > 0){
		string1 = Right(string1,string1.length - start)
	}
	var inStr = string1.indexOf(string2);
	return inStr + 1;
}
//add a number of increments to month, day or year of a date
function AddDate(interval,increment,thedate){
	if(interval == ""){
	var AddDate = "You did not supply an interval.";
		return AddDate;
	}
	else if(increment == ""){
	var AddDate = "You did not supply an increment.";
		return AddDate;
	}
	else if(thedate == ""){
	var AddDate = "You did not supply a date.";
		return AddDate;
	}
	else{
		if(thedate.indexOf("/") != -1){
		var Deliminator = "/";
		}
		if(thedate.indexOf("-") != -1){
		var Deliminator = "-";
		}
		if(thedate.indexOf(".") != -1){
		var Deliminator = ".";
		}
		if(interval == "d"){
					var datepart = thedate.split(Deliminator);
					var olddate = new Date(datepart[2],(Number(datepart[0])-1),(Number(datepart[1])+Number(increment))); //up the day a interval number
					var AddDate = (olddate.getMonth()+1) + "/" + olddate.getDate() + "/" + olddate.getFullYear(); //format the date for return in the same format received in
					return AddDate;
		}
		if(interval == "m"){
					var datepart = thedate.split(Deliminator);
					var olddate = new Date(datepart[2],((Number(datepart[0])-1) + Number(increment)),(Number(datepart[1])-1)); //up the month a interval number
					var AddDate = (olddate.getMonth()+1) + "/" + (olddate.getDate()+1) + "/" + olddate.getFullYear(); //format the date for return in the same format received in
					return AddDate;
		}
		if(interval == "y"){
					var datepart = thedate.split(Deliminator);
					var olddate = new Date((Number(datepart[2]) + Number(increment)),(Number(datepart[0])-1),(Number(datepart[1])-1)); //up the year a interval number
					var AddDate = (olddate.getMonth()+1) + "/" + (olddate.getDate()+1) + "/" + olddate.getFullYear(); //format the date for return in the same format received in
					return AddDate;
		}
	}
}
//return the differance between two dates in days, months or years
function Datedif(interval,date1,date2){
	if(interval == ""){
		var Datedif = "You must supply an interval.";
		return Datedif;
	}
	else if(date1 == ""){
		var Datedif = "You must supply the first date.";
		return Datedif;
	}
	else if(date2 == ""){
		var Datedif = "You must supply the second date.";
		return Datedif;
	}
	else{
		if(interval == "d"){
			var datepart = date1.split("/");
			var dateone = new Date(datepart[2],datepart[0],datepart[1]);
			var datepart = date2.split("/");
			var datetwo = new Date(datepart[2],datepart[0],datepart[1]);
			var difference = dateone-datetwo;//unit is milliseconds
			var Datedif = Math.round(difference/1000/60/60/24); //now unit is days
			return Datedif;
		}
		else if(interval == "m"){
			var datepart1 = date1.split("/");
			var dateone = new Date(datepart1[2],datepart1[0]-1,datepart1[1]);
			var datepart2 = date2.split("/");
			var datetwo = new Date(datepart2[2],datepart2[0]-1,datepart2[1]);
			var Yeardif = (datetwo.getFullYear() - dateone.getFullYear()) * 12; //turn year diff into months
			var Monthdif = datetwo.getMonth() - dateone.getMonth(); // get months diff
			var Datedif = Yeardif + Monthdif; //add months
			return Datedif;
		}
		else if(interval == "y"){
			var datepart1 = date1.split("/");
			var datepart2 = date2.split("/");
			var Datedif = datepart2[2] - datepart1[2]; //get year diff
			return Datedif;
		}
	}
}
//End Of My VB Functions ---------------------------------------------------------------
```

