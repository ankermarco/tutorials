# Equatable
A type that can be compared for value equality.

## Overview
Types that conform to the Equatable protocol can be compared for equality using the equal-to operator (==) or not-equal-to operator (!=).
Most basic types in the Swift standard library conform to Equatable.

## Conforming to the Equatable Protocol (Custom Type)
Adding Equatable conformance to your custom types means that _you can use more convenient APIs when __searching__ for
 particular instances __in a collection___
     
     struct StreetAddress
     {
         let number: String
         let street: String
         let unit: String?
         
         init(_ number: String, _ street: String, unit: String? = nil)
         {
             self.number = number
             self.street = street
             self.unit = unit
         }
     }
Now suppose you have an array of addresses that you need to cherck for a particular address. To use the contains(_:) method 
without including a closure in each call, extend the StreetAddress type to conform to Equatable.

    extension StreetAddress: Equatable
    {
        static func == (lhs: StreetAddress, rhs: StreetAddress) -> Bool
        {
            return
                lhs.number == rhs.number &&
                lhs.street == rhs.street &&
                lhs.unit == rhs.unit
        }
    }
    
The StreetAddress type now conforms to Equatable. You can use == to check for equality between any two instances or call 
the Equatable-constrained contains(_:) method.

    let addresses = [StreetAddress("1490","London Road"),
                     StreetAddress("566","Chiswick High Road"),
                     StreetAddress("5","Hammersimith Grove")
                    ]
    let home = StreetAddress("566","Chiswick High Road")
    
    print(addresses[0] == home) //Prints false
    print(addresses.contains[home]) //Prints true
    
