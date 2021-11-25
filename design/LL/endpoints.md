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

### Get all employees:
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
    employees: list[SingleEmployee] = [
        SingleEmployee(
            employee_id: str = "1234567890abcdefg"
            name: str = "Úlfur Örn Björnsson",
            security_number: int = 2811002110
        ),
        ...  
    ]
)
```


###






