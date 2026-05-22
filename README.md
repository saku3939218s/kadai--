# kadai--
---
config:
  layout: elk
---
classDiagram
direction TB
    class TicketVendor {
	    -Items:List
	    -cart Cart
	    +showItems() :void
	    +addItemYoCart(int itemld) :void
	    +showCartItems() :void
	    +calcChange(int payment) :void
    }

    class Main {
	    +Main
    }

    class Cart {
	    -cartItems:List
	    +addItem(Item item) :void
	    +getCartItems() :List
	    +getTotalPrice() :int
    }

    class Item {
	    -id:int
	    -name:String
	    -price:int
    }

    class UntitledClass {
	    -id:int
	    -name:String
	    -price:int
	    -quantity:int
    }

    TicketVendor <|-- Main
    TicketVendor <|-- Cart
    TicketVendor <|-- Item
    Cart -- UntitledClass
