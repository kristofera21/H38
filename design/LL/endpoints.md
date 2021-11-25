# Endpoints:

### Employees:
* GET  /employees
* POST /employees
* GET  /employees/{employee_id}
* PUT  /employees/{employee_id}


### Locations:
* GET  /locations
* POST /locations
* GET  /locations/{location_id}
* PUT  /locations/{location_id}


### Properties:
* GET  /properties
* POST /properties
* GET  /properties/{property_id}
* PUT  /properties/{property_id}
* POST /properties/{property_id}/work_request
* GET  /properties/{property_id}/facilities
* POST /properties/{property_id}/facilities
* GET  /properties/{property_id}/facilities/{facility_id}
* PUT  /properties/{property_id}/facilities/{facility_id}


### Work Requests:
* GET  /requests
* POST /requests 
* GET  /requests/{request_id}
* PUT  /requests/{request_id}


### Work Reports:
* GET  /reports
* POST /reports
* GET  /reports/{report_id}
* PUT  /reports/{report_id}
* POST /reports/{report_id}/approve
* POST /reports/{report_id}/disapprove


### Contractors:
* GET  /contractors
* POST /contractors
* GET  /contractors/{contractor_id}
* PUT  /contractors/{contractor_id}





## Employees:

### Get All Employees:
This method should return all the employees in the system. It should be accessible
to all the users in the system. It should provide four optional parameters that
should come in pairs:
* Filter parameters:
    * filter_by - This parameter should take in an Enum that tells us by what field we
    are filtering (Location).
    * filter - This parameter should take in the ID of the object we are filtering by.
    For example, in the case of finding all employees from a specific location, this
    parameter would hold the ID of said location.
* Search parameters:
    * search_by - This parameter should take in a string that tells us by what field we
    are searching (name, ssn, phone, etc...).
    * search - This parameter should take in the value we are actually searching by.

This method should then return the following:
```
EmployeeList(
    count: int = 25,
    employees: list[SimpleEmployee] = [
        SimpleEmployee(
            employee_id: str = "1234567890abcdefg"
            name: str = "Úlfur Örn Björnsson",
            security_number: int = 2811002110,
            work_phone: int = 6627880
        ),
        ...  
    ]
)
```


### Create Employee:
This method should create an employee in the system. It should take in a single
parameter that is the create employee model. This input looks like the following:
```
CreateEmployeeInput(
    name: str = "Úlfur Örn Björnsson",
    security_number: int = 2811002110,
    address: str = "Heiðargerði 21",
    home_phone: int = 5812345,
    work_phone: int = 6627880,
    email: str = "ulfurinn@gmail.com",
    location_id: str = "123456789abcdef"
)
```
The system will additionally check for a few constraints:
* The user must be a supervisor (Forbidden)
* The social security number is unique (BadRequest)
* The location ID exists in the system (NotFound)
* Any other validation requirements we decide to implement (TBD)

Afterwards the system will respond with a detailed employee model:
```
DetailEmployee(
    employee_id: str = "1234567890abcdef"
    name: str = "Úlfur Örn Björnsson",
    security_number: int = 2811002110,
    address: str = "Heiðargerði 21",
    home_phone: int = 5812345,
    work_phone: int = 6627880,
    email: str = "ulfurinn@gmail.com",
    location: BasicLocation = BasicLocation(
        location_id: str = "123456789abcdef",
        country: str = "Iceland",
        airport: str = "Keflavík, Airport",
        supervisor_id: str = "123456789abcdef"
    )
)
```


### Get Employee:
This method should get an input of a single employee ID. It should be available to
all users and should check for the following constraints:
* The employee ID provided should exist in the system (NotFound)

The system should then give the following response:
```
DetailEmployee(
    employee_id: str = "1234567890abcdef"
    name: str = "Úlfur Örn Björnsson",
    security_number: int = 2811002110,
    address: str = "Heiðargerði 21",
    home_phone: int = 5812345,
    work_phone: int = 6627880,
    email: str = "ulfurinn@gmail.com",
    location: BasicLocation = BasicLocation(
        location_id: str = "123456789abcdef",
        country: str = "Iceland",
        airport: str = "Keflavík, Airport",
        supervisor_id: str = "123456789abcdef"
    )
)
```


### Update Employee:
This method should update an employee in the system. It should take in a single
parameter that is the update employee model. This input looks like the following:
```
UpdateEmployeeInput(
    name: str = "Úlfur Örn Björnsson",
    address: str = "Heiðargerði 21",
    home_phone: int = 5812345,
    work_phone: int = 6627880,
    email: str = "ulfurinn@gmail.com",
    location_id: str = "123456789abcdef"
)
```
The system will additionally check for a few constraints:
* The user must be a supervisor (Forbidden)
* The location ID exists in the system (NotFound)
* Any other validation requirements we decide to implement (TBD)

Afterwards the system will respond with a detailed employee model:
```
DetailEmployee(
    employee_id: str = "1234567890abcdef"
    name: str = "Úlfur Örn Björnsson",
    security_number: int = 2811002110,
    address: str = "Heiðargerði 21",
    home_phone: int = 5812345,
    work_phone: int = 6627880,
    email: str = "ulfurinn@gmail.com",
    location: BasicLocation = BasicLocation(
        location_id: str = "123456789abcdef",
        country: str = "Iceland",
        airport: str = "Keflavík, Airport",
        supervisor_id: str = "123456789abcdef"
    )
)
```




