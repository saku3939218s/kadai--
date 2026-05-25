```mermaid
classDiagram

class TicketVendor {
    -Items : List
    -cart : Cart
    +showItems() : void
    +addItemToCart(int itemId) : void
    +showCartItems() : void
    +calcChange(int payment) : void
}

class Main {
    +Main()
}

class Cart {
    -cartItems : List
    +addItem(Item item) : void
    +getCartItems() : List
    +getTotalPrice() : int
}

class Item {
    -id : int
    -name : String
    -price : int
}

class CartItem {
    -id : int
    -name : String
    -price : int
    -quantity : int
}

TicketVendor --> Main
TicketVendor --> Cart
TicketVendor --> Item
Cart *-- CartItem
```
```
---
config:
  theme: forest
---
sequenceDiagram
    actor ore as 人（ユーザー）
    participant Main as :Main
    participant TicketVendor as :TicketVendor
    participant Item as :Item
    participant Cart as :Cart
    participant CartItem as :CartItem

    activate Main
    Main->>+TicketVendor: new
    TicketVendor->>+Item: new
    TicketVendor-->>-Item: 
    TicketVendor->>+Cart: new
    TicketVendor-->>-Cart: 
    TicketVendor-->>-Main: 

    Main->>+TicketVendor: showItems()
    TicketVendor-->>-Main: 

    loop 商品番号入力
        ore->>+Main: 商品番号入力
        Main->>+TicketVendor: addItemToCart(id)
        TicketVendor->>+Cart: addItem(item)
        
        opt 同じ商品がある場合は数量を変更する
            Cart->>+CartItem: new
            CartItem-->>-Cart: 
        end
        
        Cart-->>-TicketVendor: 
        TicketVendor-->>-Main: 
        Main-->>-ore: 
    end

    Main->>+TicketVendor: showCartItems()
    TicketVendor->>+Cart: getCartItems()
    Cart-->>-TicketVendor: 
    TicketVendor->>+Cart: getTotalPrice()
    Cart-->>-TicketVendor: 
    TicketVendor-->>-Main: 

    ore->>+Main: 投入金額入力
    Main->>+TicketVendor: calcChange(payment)
    TicketVendor->>+Cart: getTotalPrice()
    Cart-->>-TicketVendor: 
    TicketVendor-->>-Main: 
    Main-->>-ore: 

    deactivate Main
```
