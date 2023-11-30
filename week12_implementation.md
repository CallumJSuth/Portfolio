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
        // Arrange
        var processor = new RequestProcessor();
        var request = new OperationRequest { /* valid request data */ };

        // Act
        var result = processor.ProcessRequest(request);

        // Assert
        Assert.Equal(RequestResult.Success, result);
    }

    [Fact]
    public void ProcessRequest_InvalidRequest_ReturnsFailure()
    {
        // Arrange
        var processor = new RequestProcessor();
        var request = new OperationRequest { /* invalid request data */ };

        // Act
        var result = processor.ProcessRequest(request);

        // Assert
        Assert.Equal(RequestResult.Failure, result);
    }

    [Fact]
    public void AssignEquipment_ValidOperationAndEquipment_ReturnsTrue()
    {
        // Arrange
        var manager = new EquipmentManager();
        var operationId = "validOperationId";
        var equipmentId = "validEquipmentId";

        // Act
        var result = manager.AssignEquipment(operationId, equipmentId);

        // Assert
        Assert.True(result);
    }

    [Fact]
    public void AssignEquipment_OperationNotFound_ReturnsFalse()
    {
        // Arrange
        var manager = new EquipmentManager();
        var operationId = "nonExistentOperationId";
        var equipmentId = "validEquipmentId";

        // Act
        var result = manager.AssignEquipment(operationId, equipmentId);

        // Assert
        Assert.False(result);
    }

    [Fact]
    public void AssignEquipment_EquipmentNotFound_ReturnsFalse()
    {
        // Arrange
        var manager = new EquipmentManager();
        var operationId = "validOperationId";
        var equipmentId = "nonExistentEquipmentId";

        // Act
        var result = manager.AssignEquipment(operationId, equipmentId);

        // Assert
        Assert.False(result);
    }

    [Theory]
    [InlineData("validOperationId", "")]
    [InlineData("", "validEquipmentId")]
    [InlineData("", "")]
    public void AssignEquipment_InvalidParameters_ReturnsFalse(string operationId, string equipmentId)
    {
        // Arrange
        var manager = new EquipmentManager();

        // Act
        var result = manager.AssignEquipment(operationId, equipmentId);

        // Assert
        Assert.False(result);
    }

    // Additional tests can be written to cover edge cases, such as:
    // - Assigning equipment that is already assigned to another operation
    // - Handling of concurrent requests for the same equipment
    // - Timeouts and error handling in case of database failures
}

```
The xUnit tests validate both the request processing and equipment assignment functionalities. The first test ensures that valid requests are processed successfully, while the second test checks that equipment is correctly assigned to an operation.

## Test Code Summary

I've expanded our xUnit test suite this week to cover a spectrum of scenarios, from handling legitimate requests to dealing with potential errors like missing operations or equipment, and even incorrect input parameters. I took advantage of xUnit's [Theory] and [InlineData] attributes to run tests across a variety of input combinations, which has bolstered the robustness of our testing procedures.

I organized the tests using the Arrange-Act-Assert pattern, which has brought clarity and structure to the test cases. This approach has improved the readability and maintenance of our tests by clearly separating the setup phase, the execution of the functionality we're testing, and the subsequent result verification.

By thoroughly testing for a wide array of conditions, I've bolstered our confidence in the resilience and reliability of our code. This comprehensive testing is crucial, as it ensures that we're prepared for different operational realities and that our system behaves as expected, no matter the situation.

I plan to continue refining these tests, adding additional cases for edge conditions and specific behaviors unique to our system that may not yet be covered. It's this thorough and critical approach to testing that underpins robust and reliable software development.

## Code Review 
Feedback from the code review highlighted the need for better error handling and logging in both the RequestProcessor and EquipmentManager classes. I enhanced the error handling mechanisms and integrated detailed logging to improve traceability and ease of debugging. Adding these helped my code as a whole and allowed for better modularity.  

## Peer Code Review
In reviewing a colleague's code, I noticed a lack of validation for equipment availability. I suggested incorporating checks to ensure that equipment is not double-booked, enhancing the reliability of the assignment process. I have been told that this request will be implemented into their code before sumbission. 

## Reflective Summary
This task reinforced the importance of testing and in=depth error handling in system development. I gained insights into the nuances of resource management in operational contexts and recognized the value of rigorous testing in ensuring system integrity due to my classmates feedback. Our team's collaborative approach in code reviews has significantly improved the robustness of our solutions, paving the way for more efficient and secure operational processes.


## Screenshot of Issue 
![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss8-1.png)
