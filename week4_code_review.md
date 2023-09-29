##Code Used for Review : 
```
public void Register(string username, string password){ 
  var salt = CreateSalt(); 
  var hashedPassword = HashPassword(password, salt); 
  SaveToDatabase(username, hashedPassword, salt); 
} 

public bool Login(string username, string password){ 
  var user = GetUserFromDatabase(username); 
  var hashedPassword = HashPassword(password, user.Salt); 

  if(user.HashedPassword == hashedPassword){ 
    return true; 
  } 
  return false; 
}
```
##Optimised/Fixed Code: 
```
public void Register(string username, string password)
{
    var (hashedPassword, salt) = HashPasswordWithSalt(password);
    SaveToDatabase(username, hashedPassword, salt);
}

public bool Login(string username, string password)
{
    var user = GetUserFromDatabase(username);
    var hashedPassword = HashPassword(password, user.Salt);
    return user.HashedPassword == hashedPassword;
}

private (string HashedPassword, string Salt) HashPasswordWithSalt(string password)
{
    var salt = CreateSalt();
    var hashedPassword = HashPassword(password, salt);
    return (hashedPassword, salt);
}
```

## Explaining my process 

When looking at the code snippet provided, a couple issues/potential optimisations occur when looking at it from an analytical standpoint. First and foremost is the repeating of the line of code :  

var hashedPassword = HashPassword(password, user.Salt); 

This is a direct breach of the software principle DRY (Don’t repeat yourself) as it is reusing the HashPassword object. This causes a problem as using the same code twice can lead to future issues as adding any minor change to the HashPassword object could have unforeseen effects on both the Login and Register objects.

To get around this issue, the HashPasswordWithSalt object is created in order to allow for adjustments specific to the Register object without affecting the Login object. This is the main and biggest flaw in the code provided. Making this change should hopefully lead to a better structured and more easily adjusted piece of code. 

However, other optimisations can be made. For example, simplifying the IF statement in order to just return a Boolean value based on one comparison of code. The reason this may want to be changed is that IF statements can lead to code maintainability or readability issues in the future if anything were to be changed or added. 

Finally, the only other thing I would add is that having the salt creation and hashing of password in the Login function could be perceived as bad coding practice. This is because the register object could need extra steps added to it in the future and having the password hashing also be contained in it might lead to confusion. Having it in its own object allows it to be more easily understood, read and added to.  
