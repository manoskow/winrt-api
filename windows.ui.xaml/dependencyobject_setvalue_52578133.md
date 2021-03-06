---
-api-id: M:Windows.UI.Xaml.DependencyObject.SetValue(Windows.UI.Xaml.DependencyProperty,System.Object)
-api-type: winrt method
---

<!-- Method syntax
public void SetValue(Windows.UI.Xaml.DependencyProperty dp, System.Object value)
-->

# Windows.UI.Xaml.DependencyObject.SetValue

## -description
Sets the local value of a dependency property on a [DependencyObject](dependencyobject.md).

## -parameters
### -param dp
The identifier of the dependency property to set.

### -param value
The new local value.

## -remarks
If the provided *value* type does not match the type that is declared for the dependency property as it was originally registered, an exception is thrown.

Not all Windows Runtime properties as used by XAML are dependency properties. A [DependencyProperty](dependencyproperty.md) identifier needs to exist and it must be available as a public property of an owning object, typically the object that registered the property.

For app user-code, calling [SetValue](dependencyobject_setvalue_52578133.md) is not typically necessary. Usually, a Windows Runtime dependency property or a custom dependency property has a conventional property that wraps it, and you can just set the property value through a conventional dotted usage. Cases where you might still use [SetValue](dependencyobject_setvalue_52578133.md) are:
+ You are defining a custom dependency property. You will call [SetValue](dependencyobject_setvalue_52578133.md) as part of defining your own property set accessor for a conventional property usage. For more info, see [Custom dependency properties](http://msdn.microsoft.com/library/5adf7935-f2cf-4bb6-b1a5-f535c2ed8ef8).
+ You are defining a callback or are in some other scope where you are already being passed a [DependencyProperty](dependencyproperty.md) identifier, and it is possible that more than one dependency property exists that you might want to interact with in that scope. In these cases it is probably simpler to call [SetValue](dependencyobject_setvalue_52578133.md), passing the identifier.


## -examples

## -see-also
[Custom dependency properties](http://msdn.microsoft.com/library/5adf7935-f2cf-4bb6-b1a5-f535c2ed8ef8), [Dependency properties overview](http://msdn.microsoft.com/library/ad649e66-f71c-4daa-9994-617c886fda7e), [XAML user and custom controls sample](http://go.microsoft.com/fwlink/p/?linkid=238581)