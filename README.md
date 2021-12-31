# Just quick hackathon

trying to solve the complicated system of TA

that all

## The input

The input of the System will be something like this
(acroding from the msg that TA unit told me to fill)

### define object

#### mouth
The input that going to list the avlible day that can billing in each mouth
```
mouth : {
	mouthName : String,
	dayInMouth : [
		date {
			dateName : String (Nov-1)
			avalible : boolean (true mean can bill, false mean cannot)
		}
	],	
}
```
#### reposiblity
the course reposiblity for each
```
reposiblity : {
	courseID : String,
	courseDate : [Date],
	courseTime : {
		startTime : Time,
		endTime : Time,
		total : double
	}
}
```

### The input part
```
{
    workingMouth : [mouth],
    ta : {
    	name: String,
	studentID : String,
	reposiblity : [reposiblity]
    },
    rate : double
}
```

## The output

will look similar like [this](https://docs.google.com/spreadsheets/d/1LZtHnBSCmYy_tjWr7-p_YE5jvhef96re/edit#gid=1228444358) ,but in pdf

# Status : WIP
