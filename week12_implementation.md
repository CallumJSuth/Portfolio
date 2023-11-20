# Portfolio Entry: Week 12 - Vehicle and Equipment Assignment System

## Issue Summary
This week, I took on an the challange of creating a system for assigning vehicles and equipment to our operations teams. The main aim was to ccreate a section of the database which will streamline the process of this . It was all about making sure that every request they sent in was handled smoothly and efficiently, ensuring we use our resources wisely and effectively. The idea was to streamline the whole process, from request to deployment, so our teams can focus on their missions without worrying about the logistics of equipment and vehicle availability.

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
This C# snippet illustrates the ProcessRequest method, which checks the validity of requests and equipment availability before assigning equipment to operations. It encapsulates key aspects of request processing, ensuring efficient and error-free handling.

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

Here, the AssignEquipment method in the EquipmentManager class is responsible for the actual assignment of equipment to operations. It ensures that both the operation and the equipment exist before proceeding with the assignment.

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
The xUnit tests validate both the request processing and equipment assignment functionalities. The first test ensures that valid requests are processed successfully, while the second test checks that equipment is correctly assigned to operations.

## Test Code Summary
The xUnit tests are integral in validating the functionality of the vehicle and equipment assignment system. They cover scenarios like processing valid and invalid requests and assigning equipment to valid operations, ensuring the system's robustness and reliability in resource allocation.

## Code Review 
Feedback from the code review highlighted the need for better error handling and logging in both the RequestProcessor and EquipmentManager classes. I enhanced the error handling mechanisms and integrated detailed logging to improve traceability and ease of debugging. Adding these changed 

## Peer Code Review
In reviewing a colleague's code, I noticed a lack of validation for equipment availability. I suggested incorporating checks to ensure that equipment is not double-booked, enhancing the reliability of the assignment process.

## Reflective Summary
This task reinforced the importance of testing and in=depth error handling in system development. I gained insights into the nuances of resource management in operational contexts and recognized the value of rigorous testing in ensuring system integrity. Our team's collaborative approach in code reviews has significantly improved the robustness of our solutions, paving the way for more efficient and secure operational processes.


## Screenshot of Issue 
![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss8-1.png)
