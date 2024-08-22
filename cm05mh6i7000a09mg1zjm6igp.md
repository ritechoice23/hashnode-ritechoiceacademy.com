---
title: "Clean & Scalable Code in Laravel: Practical Tips with Examples"
seoTitle: "Laravel: Practical Tips for Clean & Scalable Code"
seoDescription: "Tips for clean, scalable Laravel code: use naming conventions, single responsibility principle, avoid magic numbers, and organize code logically"
datePublished: Thu Aug 22 2024 18:34:54 GMT+0000 (Coordinated Universal Time)
cuid: cm05mh6i7000a09mg1zjm6igp
slug: clean-scalable-code-in-laravel-practical-tips-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/jG8nlwLRZTM/upload/7a990a3990c893f05e681b5fa5faed99.jpeg
tags: laravel, php, phpstorm, codequality, php8, laraveldevelopment, laravelframework, code-readability

---

What does clean and scalable code look like in practice? In this tutorial, I'll share from experience some actionable tips for writing clean code in Laravel or software development generally.

The aim is to ensure that the code we write is easy to understand and maintain for both ourselves and future developers.

## 1\. Naming Things

Naming things is crucial and is likely the hardest thing in programming.

It is very important to use descriptive and specific names for your variables, functions, and classes. It’s the first step to clear, understandable code.

### Variable & Functions

Naming variables and functions effectively is also a key to writing clean, maintainable code, let’s take a look at some examples

* **Make it Descriptive Over Cryptic**
    
    **Bad**:
    
    ```php
    public function calculate()
    {
        $p = request('pid');
        $d = request('dt');
        $t = Product::find($p);
        $r = $this->computeRevenue($t, $d);
    
        return $r;
    }
    
    ```
    
    Forward to the next 6 months if you or another person visit this code your question will be What do `$p`, `$d`, and `$t` represent? This ambiguity can lead to confusion and potential errors down the line.
    
    **Good**:
    
    ```php
    public function calculateRevenue()
    {
        $productId = request('product_id');
        $dateRange = request('date_range');
        $product = Product::find($productId);
        $revenue = $this->computeRevenueForProduct($product, $dateRange);
    
        return $revenue;
    }
    
    ```
    
    Here, `$productId`, `$dateRange`, and `$product` are immediately clear, reducing the need for additional context. The function name `calculateRevenue` also **clearly indicates its purpose.**
    
* **Longer Names**
    
    When naming functions or variables, clarity should be your top priority. Longer names that describe the purpose clearly are far better than short, cryptic ones. For example:
    
    ```php
    // Good: Detailed and self-explanatory
    public function sendEmailToInactiveUsersInRegion(string $region, int $inactiveDays)
    {
        // processing logic
    }
    
    ```
    
    Though the function name is long, it’s instantly understandable. It tells you exactly what the function does, who it targets, and under what conditions.
    

### Routes

Use kebab-case for public-facing URLs. `/php-frameworks`

* **Route Names**
    

Use camelCase for route names.

`Route::get('/php-frameworks', [FrameworkController::class, 'index'])->name('phpFramework');`

* **Route Parameters**
    

Use camelCase for route parameters.

`Route::get('news/{newsItem}', [NewsController::class, 'index']);`

* **Slash in URLs**
    
    Avoid starting a route URL with a slash (`/`) unless the URL is an empty string.
    

**Good**:

* `Route::get('/', [HomeController::class, 'index']);`
    
* `Route::get('/php-frameworks', [FrameworkController::class, 'index'])->name('phpFramework');`
    

**Bad**:

* `Route::get('', [HomeController::class, 'index']);`
    
* `Route::get('php-frameworks', [FrameworkController::class, 'index'])->name('phpFramework');`
    

### **2\. Stick to the Single Responsibility Principle**

Each class or function should have a clear purpose and one reason to change. This keeps your code focused and easier to debug.

**Bad:**

```php
class UserRegistrationService
{
    public function register(array $data)
    {
        // Validate the data
        if (!$this->isValid($data)) {
            throw new \\Exception('Invalid data');
        }

        // Create the user
        $user = new User();
        $user->name = $data['name'];
        $user->email = $data['email'];
        $user->password = Hash::make($data['password']);
        $user->save();

        // Send a welcome email
        Mail::to($user->email)->send(new WelcomeEmail($user));

        return $user;
    }

    private function isValid(array $data)
    {
        // Validation logic here
    }
}
```

**Good:**

```php
class RegisterUserAction
{
    private $validateUserAction;
    private $createUserAction;
    private $sendWelcomeEmailAction;

    public function __construct(ValidateUserAction $validateUserAction, CreateUserAction $createUserAction, SendWelcomeEmailAction $sendWelcomeEmailAction)
    {
        $this->validateUserAction = $validateUserAction;
        $this->createUserAction = $createUserAction;
        $this->sendWelcomeEmailAction = $sendWelcomeEmailAction;
    }

    public function execute(array $data): User
    {
        $this->validateUserAction->execute($data);
        $user = $this->createUserAction->execute($data);
        $this->sendWelcomeEmailAction->execute($user);

        return $user;
    }
}

```

## 3\. **Avoid Magic Numbers and Strings**

Magic numbers and strings can be confusing. Replace them with constants or configuration values to improve clarity.

**Bad:**

```php
class User
{
    public function setStatus(int $status)
    {
        // Set the user's status
        $this->status = $status;
    }
}

// Usage
$user = new User();
$user->setStatus(1); // What does 1 mean?

```

**Good:**

Leveraging enums in PHP we can simplify this.

```php
enum UserStatus: int
{
    case ACTIVE = 1;
    case INACTIVE = 0;
}

class User
{
    public function setStatus(UserStatus $status)
    {
        $this->status = $status->value;
    }
}

// Usage
$user = new User();
$user->setStatus(UserStatus::ACTIVE);

```

## **4\. Reduce Complexity with Early Returns**

Simplifying methods by using early returns to handle edge cases upfront can make the core logic more readable and reduce unnecessary nesting.

### **Bad:**

```php
public function getUserProfile($id)
{
    $user = User::find($id);

    if ($user) {
        // If user exists, show the profile view
        return view('user.profile', compact('user'));
    } else {
        // If user does not exist, return an error response
        return response()->json(['error' => 'User not found'], 404);
    }
}

```

### **Good:**

```php
public function getUserProfile($id)
{
    if (!$user = User::find($id)) {
        return response()->json(['error' => 'User not found'], 404);
    }

    return response()->json($user);
}

```

## **5\. Organize Code into Logical Units**

Organizing code into actions allows you to separate concerns and create a more modular, maintainable structure. Each action is responsible for a specific task, making the application easier to understand and extend.

### **Bad:**

```php
class OrderController
{
    public function processOrder(Request $request)
    {
        // Validate input
        if (!$this->isValidOrder($request)) {
            return response()->json(['error' => 'Invalid order'], 400);
        }

        // Process the transaction
        $order = new Order();
        $order->user_id = $request->user()->id;
        $order->total = $request->total;
        $order->status = 'processed';
        $order->save();

        // Send receipt email
        Mail::to($request->user()->email)->send(new OrderReceipt($order));

        return response()->json(['success' => 'Order processed successfully'], 200);
    }

    private function isValidOrder(Request $request)
    {
        // Validation logic
    }
}

```

In this example, the `OrderController` is responsible for multiple tasks, including validation, processing, and emailing. This makes the controller bloated and less maintainable.

### **Good:**

**Custom Request Class for Validation:**

```php
namespace App\\\\Http\\\\Requests;

use Illuminate\\\\Foundation\\\\Http\\\\FormRequest;

class ProcessOrderRequest extends FormRequest
{
    public function authorize()
    {
        return true; // Or implement authorization logic
    }

    public function rules()
    {
        return [
            'total' => 'required|numeric|min:0.01',
            // Other validation rules
        ];
    }
}

```

**Controller Handling Actions:**

```php
class OrderController
{
    protected $processOrderAction;
    protected $sendReceiptAction;

    public function __construct(ProcessOrderAction $processOrderAction, SendReceiptAction $sendReceiptAction)
    {
        $this->processOrderAction = $processOrderAction;
        $this->sendReceiptAction = $sendReceiptAction;
    }

    public function processOrder(ProcessOrderRequest $request)
    {
        $order = $this->processOrderAction->execute($request);
        $this->sendReceiptAction->execute($order);

        return response()->json(['success' => 'Order processed successfully'], 200);
    }
}

```

**Action Classes:**

```php
class ProcessOrderAction
{
    public function execute(ProcessOrderRequest $request): Order
    {
        $order = new Order();
        $order->user_id = $request->user()->id;
        $order->total = $request->total;
        $order->status = 'processed';
        $order->save();

        return $order;
    }
}

class SendReceiptAction
{
    public function execute(Order $order)
    {
        Mail::to($order->user->email)->send(new OrderReceipt($order));
    }
}

```

Here, the validation logic is moved to a `ProcessOrderRequest` class, which handles all the necessary input validation. This keeps the controller clean and focused solely on coordinating the request and the actions.

* **ProcessOrderAction** handles the core business logic of processing the order.
    
* **SendReceiptAction** is responsible for sending the receipt email.
    

This structure keeps each component focused on a single responsibility, making the codebase more modular, testable, and easier to maintain.

Above are a few I have to share from experience, if you have others or questions, you can shoot in the comment below.