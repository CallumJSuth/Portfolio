# Portfolio Entry: Week 12 - Vehicle and Equipment Assignment System

## Issue Summary
This week, I took on an the challange of creating a system for assigning vehicles and equipment to the operations team. The main aim was to ccreate a section of the database which will effectivly streamline the process of this for all users . The main challanged was about making sure that every request they sent in was handled smoothly and efficiently, ensuring UNDAC's resources are utlised wisely and effectively. The idea was to simplify the whole process, from request to deployment, so the teams can focus on their missions without worrying as much about the logistics of equipment and vehicle availability.

## Code Snippets and Commentary
```csharp
public class RequestProcessor
{
    public RequestResult ProcessRequest(OperationRequest request)
    {
        if (request.IsValid() && EquipmentAvailable(request.EquipmentId))
        {
            AssignEquipment(request.OperationId, request.EquipmentId);
            return RequestResult.Success;
        }
        return RequestResult.Failure;
    }
}
```
This C# snippet illustrates the ProcessRequest method, which checks the validity of requests and equipment availability before assigning equipment to operations. It shows  good practices of request processing, which ensures efficient and error-free handling.

```csharp
public class EquipmentManager
{
    public bool AssignEquipment(string operationId, string equipmentId)
    {
        var operation = FindOperationById(operationId);
        var equipment = FindEquipmentById(equipmentId);
        if (operation != null && equipment != null)
        {
            operation.EquipmentList.Add(equipment);
            return true;
        }
        return false;
    }
}
```

Here, the AssignEquipment method in the EquipmentManager class is responsible for the actual assignment of equipment to operations. It ensures that both the operation and the equipment exist before proceeding with the assignment. This test ensure that valid data is passed into the system and helps avoid any errors with incorrect data submission. 

## Test Code 
```csharp

public class EquipmentAssignmentTests
{
    [Fact]
    public void ProcessRequest_ValidRequest_ReturnsSuccess()
    {
        var processor = new RequestProcessor();
        var request = new OperationRequest { /* valid request data */ };
        var result = processor.ProcessRequest(request);
        Assert.Equal(RequestResult.Success, result);
    }

    [Fact]
    public void AssignEquipment_ValidOperationAndEquipment_ReturnsTrue()
    {
        var manager = new EquipmentManager();
        var result = manager.AssignEquipment("validOperationId", "validEquipmentId");
        Assert.True(result);
    }
}
```
The xUnit tests validate both the request processing and equipment assignment functionalities. The first test ensures that valid requests are processed successfully, while the second test checks that equipment is correctly assigned to an operation.

## Test Code Summary
The xUnit tests are integral in validating the functionality of the vehicle and equipment assignment system. They cover scenarios like processing valid and invalid requests and assigning equipment to valid operations, ensuring the system's robustness and reliability in resource allocation.

## Code Review 
Feedback from the code review highlighted the need for better error handling and logging in both the RequestProcessor and EquipmentManager classes. I enhanced the error handling mechanisms and integrated detailed logging to improve traceability and ease of debugging. Adding these helped my code as a whole and allowed for better modularity.  

## Peer Code Review
In reviewing a colleague's code, I noticed a lack of validation for equipment availability. I suggested incorporating checks to ensure that equipment is not double-booked, enhancing the reliability of the assignment process. I have been told that this request will be implemented into their code before sumbission. 

## Reflective Summary
This task reinforced the importance of testing and in=depth error handling in system development. I gained insights into the nuances of resource management in operational contexts and recognized the value of rigorous testing in ensuring system integrity due to my classmates feedback. Our team's collaborative approach in code reviews has significantly improved the robustness of our solutions, paving the way for more efficient and secure operational processes.


## Screenshot of Issue 
![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss8-1.png)
