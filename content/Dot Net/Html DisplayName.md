**`DisplayFor`**:

- A method provided by the `HtmlHelper` class that generates HTML markup for displaying the value of a specified property in the model.
- It takes into account any formatting or display templates associated with the property's type.


![[Pasted image 20241208134059.png]]

 What This Does:

- ==**`@Html.DisplayFor(modelItem => i.Name)`** will output the value of the `Name` property for each `Person` object in the `Model` collection.==
- It respects any formatting or custom display templates that might be associated with the `Name` property. For example, if there was a `[DisplayFormat]` attribute or a custom display template for `string` types, `DisplayFor` would apply that formatting.

### Key Points:

- **Formatting**: `DisplayFor` is particularly useful when you want to ensure that the property value is displayed with consistent formatting across your application. This could include date formatting, currency formatting, or any other custom formats you've defined.
    
- **Custom Display Templates**: If you have a custom display template for a property type, `DisplayFor` will automatically use that template to render the property. This is useful for creating reusable, consistent UI components.