
# Week 11

## Issue Summary
This week's focus was on the feature of reinstating system access for users returning to the team. The goal was to ensure controlled access and robust data security, with the Deputy Team Leader required to approve access reinstatements.

## Code Snippets and Commentary

```xaml
<Window x:Class="AccessReinstatementWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Access Reinstatement" Height="300" Width="300">
    <Grid>
        <Label x:Name="UserIdLabel" Content="User ID:" HorizontalAlignment="Left" Margin="10,10,0,0"/>
        <TextBox x:Name="UserIdTextBox" HorizontalAlignment="Left" Margin="70,10,0,0" Width="200"/>
        <Button x:Name="RequestAccessButton" Content="Request Access" HorizontalAlignment="Left" Margin="10,40,0,0" Click="RequestAccessButton_Click"/>
        <TextBlock x:Name="ResultTextBlock" HorizontalAlignment="Left" Margin="10,70,0,0"/>
    </Grid>
</Window>
```
This code snippet shows the user interface for requesting access reinstatement. It includes a text box for entering the user ID and a button to submit the request. The layout is straightforward, ensuring ease of use.

```csharp
private void RequestAccessButton_Click(object sender, RoutedEventArgs e)
{
    string userId = UserIdTextBox.Text;
    if (IsReturningMember(userId))
    {
        SendApprovalRequest(userId, deputyTeamLeaderId);
        ResultTextBlock.Text = "Request sent for approval";
    }
    else
    {
        ResultTextBlock.Text = "Access request denied";
    }
}
```
In the corresponding C# code, `RequestAccessButton_Click` function captures the user ID from the text box and checks if the user is a returning member. Depending on this check, it sends an approval request or denies access.

## Test Code

```
public class AccessReinstatementTests
{
    [Fact]
    public void RequestReinstatement_ReturningMember_ShouldSendApproval()
    {
        var result = RequestAccessReinstatement(returningMemberId);
        Assert.Equal("Request sent for approval", result);
    }

    [Fact]
    public void RequestReinstatement_NonMember_ShouldDenyAccess()
    {
        var result = RequestAccessReinstatement(nonMemberId);
        Assert.Equal("Access request denied", result);
    }
}
```

These tests are to ensure access reinstatement effectively checks requests from team members who are coming back and securely rejects those who are not members, making sure the system remains secure. It verifies that the system can effectively manage access control while maintaining a balance between reintegrating users and ensuring strong data security. This thorough testing approach strengthens the system's security and prioritises the end users of this program.

## Code Review and Fixes
Feedback from the code review highlighted the need for better handling of the Deputy Team Leader's dynamic ID. I addressed this by implementing a more flexible solution in the C# code to accommodate changes in leadership roles.

## Peer Code Review
In reviewing a peer's work, I suggested adding a detailed logging system for tracking access reinstatement requests, enhancing the accountability and traceability of our system.

## Reflective Summary
This week's task underscored the importance of robust testing and flexible design in security-critical features. Comparing my approach with my peers, I noticed a significant improvement in our team's communication and workflow efficiency. Future enhancements could involve creating a system where multiple people could review a persons code and pull their suggestions/improvments into one easy to understand format/text channel. 

## Screenshot of Issue 

![Image](https://github.com/CallumJSuth/Portfolio/blob/main/images/ss7-1.png)
