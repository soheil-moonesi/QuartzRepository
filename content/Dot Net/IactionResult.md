
![[Pasted image 20241207212432.png]]

چه از web api استفاده کنیم یا MVC controller این دوتا هر جفتشون از Controller base ارث بری میکنن و IACTION Result  رو برمیگردونن 

![[Pasted image 20241207212511.png]]

خوب اینجا داره میگه که خیلی دستمون بازه توی middleware ها 
هم pipeline سمت response و هم request از یه middleware دارن استفاده میکنن

![[Pasted image 20241207212531.png]]

#IActionResult
#ViewResult
#jsonResult


`IActionResult` is an interface in ASP.NET Core MVC that represents the result of an action method in a controller. When an action method in a controller returns a result, it can return different types of responses, such as rendering a view, redirecting to another action, returning a JSON object, or sending a file. The `IActionResult` interface provides a common way to represent all of these possible outcomes.

### Common Implementations of `IActionResult`:

Here are some common classes that implement `IActionResult`:

1. **`ViewResult`**:
    
    - Represents a rendered view.
    - Example: `return View(model);`
2. **`JsonResult`**:
    
    - Represents a JSON-formatted response.
    - Example: `return Json(data);`
3. **`RedirectResult`**:
    
    - Represents a redirection to another URL.
    - Example: `return Redirect("https://example.com");`
4. **`RedirectToActionResult`**:
    
    - Represents a redirection to another action within the same application.
    - Example: `return RedirectToAction("ActionName");`
5. **`ContentResult`**:
    
    - Represents a plain text response.
    - Example: `return Content("Hello World");`
6. **`FileResult`**:
    
    - Represents a response that contains a file (e.g., for download).
    - Example: `return File(fileBytes, "application/pdf");`
7. **`StatusCodeResult`**:
    
    - Represents a response with a specific HTTP status code.
    - Example: `return StatusCode(404);`
8. **`EmptyResult`**:
    
    - Represents a response that does not have any content.
    - Example: `return new EmptyResult();`

- ### Why Use `IActionResult`?

Using `IActionResult` as the return type in action methods gives you the flexibility to return different kinds of responses from the same method. It also adheres to the principle of programming to an interface, making your code more flexible and testable.

بهمون این قابلیت رو میده که چیزهای مختلفی رو توی return برگردونیم 

