---
title: "Interfaces - C# Programming Guide"
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords: 
  - "interfaces [C#]"
  - "C# language, interfaces"
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# Interfaces (C# Programming Guide)

An interface contains definitions for a group of related functionalities that a non-abstrat [class](../../language-reference/keywords/class.md) or a [struct](../../language-reference/keywords/struct.md) must implement.
  
By using interfaces, you can, for example, include behavior from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes. In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.  
  
You define an interface by using the [interface](../../language-reference/keywords/interface.md) keyword. as the following example shows.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md). By convention, interface names begin with a capital `I`.

Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies. As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.  
  
The definition of `IEquatable<T>` doesn’t provide an implementation for `Equals`. A class or struct can implement multiple interfaces, but a class can only inherit from a single class.
  
For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Interfaces can contain methods, properties, events, indexers, or any combination of those four member types. For links to examples, see [Related Sections](./index.md#BKMK_RelatedSections). An interface can't contain constants, fields, operators, instance constructors, finalizers, or types. Interface members are automatically public, and they can't include any access modifiers. Members also can't be [static](../../language-reference/keywords/static.md).  
  
To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.  
  
When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface defines. The interface itself provides no functionality that a class or struct can inherit in the way that it can inherit base class functionality. However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.  
  
The following example shows an implementation of the <xref:System.IEquatable%601> interface. The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface. For example, an interface might declare a property that has a [get](../../language-reference/keywords/get.md) accessor. The class that implements the interface can declare the same property with both a `get` and [set](../../language-reference/keywords/set.md) accessor. However, if the property or indexer uses explicit implementation, the accessors must match. For more information about explicit implementation, see [Explicit Interface Implementation](explicit-interface-implementation.md) and [Interface Properties](../classes-and-structs/interface-properties.md).  

Interfaces can inherit from other interfaces. A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces inherit. However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`). If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface. However, the derived class can reimplement any virtual interface members instead of using the inherited implementation.  
  
A base class can also implement interface members by using virtual members. In that case, a derived class can change the interface behavior by overriding the virtual members. For more information about virtual members, see [Polymorphism](../classes-and-structs/polymorphism.md).  
  
## Interfaces summary

An interface has the following properties:  

- An interface is like an abstract base class with only abstract members. Any class or struct that implements the interface must implement all its members.
- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.
- Interfaces can contain events, indexers, methods, and properties.
- Interfaces contain no implementation of methods.
- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

## In this section

[Explicit Interface Implementation](explicit-interface-implementation.md)  
 Explains how to create a class member that’s specific to an interface.  
  
 [How to: Explicitly Implement Interface Members](how-to-explicitly-implement-interface-members.md)  
 Provides an example of how to explicitly implement members of interfaces.  
  
 [How to: Explicitly Implement Members of Two Interfaces](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Provides an example of how to explicitly implement members of interfaces with inheritance.  
  
## <a name="BKMK_RelatedSections"></a> Related Sections

- [Interface Properties](../classes-and-structs/interface-properties.md)  
- [Indexers in Interfaces](../indexers/indexers-in-interfaces.md)  
- [How to:  Implement Interface Events](../events/how-to-implement-interface-events.md)  
- [Classes and Structs](../classes-and-structs/index.md)  
- [Inheritance](../classes-and-structs/inheritance.md)  
- [Methods](../classes-and-structs/methods.md)  
- [Polymorphism](../classes-and-structs/polymorphism.md)  
- [Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Properties](../classes-and-structs/properties.md)  
- [Events](../events/index.md)  
- [Indexers](../indexers/index.md)  
  
## featured book chapter

[Interfaces](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## See also

- [C# Programming Guide](../index.md)
- [Inheritance](../classes-and-structs/inheritance.md)
- [Identifier names](../inside-a-program/identifier-names.md)
