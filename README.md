classDiagram

class TicketVendor {
    -Items: List
    -cart: Cart
    +showItems() : void
    +addItemToCart(int itemId) : void
    +showCartItems() : void
    +calcChange(int payment) : void
}

class Main {
    +Main()
}

class Cart {
    -cartItems: List
    +addItem(Item item) : void
    +getCartItems() : List
    +getTotalPrice() : int
}

class Item {
    -id: int
    -name: String
    -price: int
}

class CartItem {
    -id: int
    -name: String
    -price: int
    -quantity: int
}

TicketVendor --> Main
TicketVendor --> Cart
TicketVendor --> Item

Cart *-- CartItem
