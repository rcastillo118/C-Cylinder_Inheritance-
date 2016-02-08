# C-Cylinder_Inheritance-
C++/using a derived class that has publicly inherited from a base class.

/***********CircleType Header************/

#include <iostream>

class circleType
{
public:
	void setRadius(double r);
	//Function to set the radius.
	//Postcondition: if (r >= 0) radius = r;
	// otherwise radius = 0;

	double getRadius();
	//Function to return the radius.
	//Postcondition: The value of radius is returned.

	double area();
	//Function to return the area of a circle.
	//Postcondition: Area is calculated and returned.

	double circumference();
	//Function to return the circumference of a circle.
	//Postcondition: Circumference is calculated and returned.

	void printCircleProperties();
	//Function to print the value of the circle's: radius, area,
	//and circumference
	//Postcondition: The radius, area, and circumference of the circle
	//are printed

	circleType(double r = 0);
	//Constructor with a default parameter.
	//Radius is set according to the parameter.
	//The default value of the radius is 0.0;
	//Postcondition: radius = r;


private:
	double radius;

};
//#endif

/***********CircleType Implementation************/

#include "circleType.h"

using namespace std;

void circleType::setRadius(double r)
{
	if (r >= 0)
		radius = r;
	else
		radius = 0;
}

double circleType::getRadius()
{
	return radius;
}

double circleType::area()
{
	return 3.1416 * radius * radius;
}

double circleType::circumference()
{
	return 2 * 3.1416 * radius;
}

void circleType::printCircleProperties()
{

	cout << "Radius: " << circleType::getRadius() << " feet." << endl << endl;
	cout << "Area: " << circleType::area() << " square feet." << endl << endl;
	cout << "Circumference: " << circleType::circumference() << " feet." << endl << endl;


}

circleType::circleType(double r)
{
	setRadius(r);
}

/******************CylinderType Header*********************/

rcastillo118
Assign #3

This is the header file for the class cylinderType. All of the function
prototypes for the class, including the private member variables, 
are printed here. Also included is the prototype of the default constructor for cylinderType. 
Although it was not neccessary for the purposes of this program, I have left a set of input 
blocks, whose purpose is to prevent the members of the base class from being defined twice in a program, 
at the top and bottom of the header file. They have been commented-out and, they are only 
there to serve me as a reminder of how to properly declare them in a program.

************************************************************************/

#include <iostream>
#include "circleType.h"

class cylinderType : public circleType
{
public:

	void setDimensions(double r, double h);
	// Funtion to set the radius of the base and height of the cylinder
	// Postcondition:
	//		radius = r;
	//		height = h;

	double getRadius();
	// Function to return the radius of the base of the cylinder
	// This function already belongs to the class circleType, so I will include
	// a call to the base class function "getRadius" in the definition of this 
	// derived class function. This way I will be able to access the value of the 
	// base class private instance variable "radius".
	// Postcondition:
	//		return radius;

	double getHeight() const;
	// Function to return the height of the cylinder
	// Postcondition:
	//		return height;

	void calculateVolume();
	// Function to calculate the volume of the cylinder by taking the radius of the base
	// and the height of the cylinder and, applying them to the equation that calculates
	// a cylinder's volume
	// Postcondition:
	//		The volume of the cylinder is calculated and stored in the private instance 
	//		variable "vol"

	void calculateSurfaceArea();
	// Function to calculate the surface area of the cylinder. In order to obtain and use 
	// the values of "radius" and "height", calls to the functions getRadius and getHeight
	// are performed and inserted into the equation used for calculating the surface area of
	// a cylinder
	// Postcondition:
	//		The surface area of the cylinder is calculated and stored in the private instance
	//		variable "sA"

	void printVolume() const;
	// Function to print the volume of the cylinder
	// Postcondition:
	//		The value stored in "vol" is printed

	void printSurfaceArea() const;
	// Function to print the surface area of the cylinder
	// Postcondition:
	//		The value stored in "sA" is printed

	cylinderType();
	// The default constructor for the objects of class cylinderType
	// The instance variable "radius" is initialized through the 
	// default constructor from class circleType
	// Postcondition:
	//		radius = 0.0;
	//		height = 0.0;
	//		vol = 0.0;
	//		sA = 0.0;

private:

	double height;
	double vol;
	double sA;
	// The private instance variables belonging to class cylinderType. "radius" is not 
	// included here because it is inherited from class circleType.
};

/*******************CylinderType Implementation*********************/

/***********************************************************************
rcastillo118
Assign #3 

This is the implementation file for the member functions of class cylinderType.
These functions describe in detail how the functions work and, how certain 
functions access other functions from the base class circleType in order to 
complete some operations. I have also included the definition of the default
constructor for this class.

************************************************************************/

#include "cylinderType.h"

using namespace std;

// declare PI as a global variable, which will be used to calculate the
// volume and surface area of the cylinder

static const double PI = 3.1416;

// Funtion to set the radius of the base and height of the cylinder
// Postcondition:
//		radius = r;
//		height = h;

void cylinderType::setDimensions(double r, double h){

	circleType::setRadius(r);

	if (h >= 0) {

		height = h;
	}
	else {

		height = 0.0;
	}

}

// Function to return the radius of the base of the cylinder
// This function already belongs to the class circleType, so I will include
// a call to the base class function "getRadius" in the definition of this 
// derived class function. This way I will be able to access the value of the 
// base class private instance variable "radius".
// Postcondition:
//		return radius;

double cylinderType::getRadius() {

	return circleType::getRadius();

}

// Function to return the height of the cylinder
// Postcondition:
//		return height;

double cylinderType::getHeight() const {

	return height;

}

// Function to calculate the volume of the cylinder by taking the radius of the base
// and the height of the cylinder and, applying them to the equation that calculates
// a cylinder's volume
// Postcondition:
//		The volume of the cylinder is calculated and stored in the private instance 
//		variable "vol"

void cylinderType::calculateVolume() {

	vol = PI * (circleType::getRadius() * circleType::getRadius() * height);

}

// Function to calculate the surface area of the cylinder. In order to obtain and use 
// the values of "radius" and "height", calls to the functions getRadius and getHeight
// are performed and inserted into the equation used for calculating the surface area of
// a cylinder
// Postcondition:
//		The surface area of the cylinder is calculated and stored in the private instance
//		variable "sA"

void cylinderType::calculateSurfaceArea() {

	sA = 2 * (PI * circleType::getRadius() * height) +
		2 * (PI * circleType::getRadius() * circleType::getRadius());

}

// Function to print the volume of the cylinder
// Postcondition:
//		The value stored in "vol" is printed

void cylinderType::printVolume() const {

	cout << "The volume of the cylinder is: ";
	cout << vol << " cubic feet." << endl << endl;

}

// Function to print the surface area of the cylinder
// Postcondition:
//		The value stored in "sA" is printed

void cylinderType::printSurfaceArea() const {

	cout << "The surface area of the cylinder is: ";
	cout << sA << " square feet." << endl << endl;

}

// The default constructor for the objects of class cylinderType
// The instance variable "radius" is initialized through the 
// default constructor from class circleType
// Postcondition:
//		radius = 0.0;
//		height = 0.0;
//		vol = 0.0;
//		sA = 0.0;


cylinderType::cylinderType() :circleType(0.0) {

	height = 0.0;
	vol = 0.0;
	sA = 0.0;

}

/************************CylinderType_Test**********************/

/*
rcastillo118
Assign #3

Problem:
I need to create a class that will obtain the properties of a cylinder, such as the radius and height. This class
will also need to perform calculations with that data in order to determine the cylinder's: volume, surface area, and the pertinent
properties of the cylinder's base. In order for me to obtain all of the data that I will need to calculate the properties 
that I've just mentioned, I will need to access the header and implementation files of the existing class "circleType".  This will make
the class that I will create a derived class of the existing class "circleType". Thus, my new class will need to inherit the members of
class "circleType" in order for me to properly arrive at a solution for a cylinder's volume and surface area. Considering all of this,
I must make sure that the circleType files that I will require in my new class are located in the same directory as my new
class. This will ensure that I'll have access to the data that I will need to set the appropriate properties of a cylinder and,
perform the necessary calculations.

Solution:
I create a class called "cylinderType". Within the header and implementation files for this class, I include the private 
instance variables and functions necessary to calculate the volume and surface area of the cylinderType object myCylinder, which I
declare in the main program.   

I first prompt the user to enter the radius and height of a cylinder (in feet), whose values will be stored in the local variables "cylinRadius" and 
"cylinHeight". These values are then input into the function "setDimensions", which takes the values of these two local variables and uses
them to set the private instances variables of circleType (radius) and cylinderType (height), thereby setting the radius and height of myCylinder.

Having the values for the radius and height of myCylinder, I can then implement the functions that I've defined to calculate the volume and
surface area of myCylinder. A call to these functions will take the values for radius and height that the user has defined and, determine the 
volume and surface area of myCylinder. After having calculated the volume and surface area of myCylinder, a call to the "print" functions for these
two values is made and, the values for the volume and surface area of myCylinder is printed to the screen.

In addition to printing the values of myCylinder's volume and surface area, I make a call to the class circleType function "printCircleProperties" 
in order to print the values of the properties of myCylinder's base, which are: radius, area, and circumference. 
*/

#include <iostream>
#include <iomanip>
#include "cylinderType.h"

using namespace std;

int main()
{
	cout << fixed << showpoint << setprecision(2);

	// declare an object of class cylinderType. This object will perform operations that
	// will obtain the radius and height of a cylinder. Other operations that the object
	// will perform are: calculating the volume and surface area of a cylinder, and printing
	// out those values.

	cylinderType myCylinder;

	// declare the local variables that will hold the values for the radius and base of the 
	// cylinder. These will be passed as parameters to the functions that calculate volume and
	// surface area. 

	double cylinRadius = 0.0;
	double cylinHeight = 0.0;

	// prompt the user to enter the radius of the cylinder

	cout << "Please enter the radius (in feet) of the cylinder: ";
	cin >> cylinRadius;
	cout << endl << endl;

	// prompt the user to enter the height of the cylinder

	cout << "Please enter the height (in feet) of the cylinder: ";
	cin >> cylinHeight;
	cout << endl << endl;

	// store the values that are currently residing in the locally declared variables "cylinRadius"
	// and "cylinHeight" inside the private instance variables "radius" and "height

	myCylinder.setDimensions(cylinRadius, cylinHeight);

	// take the data that the user input for the radius and height of myCylinder and input it into a
	// function whose purpose is to calculate the volume of the cylinder. After the function has 
	// calculated the volume of the cylinder, store that value in the cylinderType private instance
	// variable "vol"

	myCylinder.calculateVolume();

	// take the data that the user input for the radius and height of myCylinder and input it into a 
	// function whose purpose is to calculate the surface area of the cylinder. After the function has
	// calculated the surface area of the cylinder, store that value in the cylinderType private instance
	// variable "sA"

	myCylinder.calculateSurfaceArea();
	
	// print the volume and surface area of myCylinder

	myCylinder.printVolume();
	myCylinder.printSurfaceArea();
		
	// print the area and circumference of the base of myCylinder by delving into class circleType and using
	// it's functions, which calculate and return a circle's area and circumference. This circle, along with
	// it's properties, constitute the base of myCylinder

	cout << "The properties of the base of the cylinder are as follows: " << endl << endl;

	myCylinder.printCircleProperties();

	return 0;
}
