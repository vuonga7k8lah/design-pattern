# Clean Code PHP

## Mục lục

  1. [Giới thiệu](#giới-thiệu)
  2. [Biến](#biến)
     * [Sử dụng tên biến có ý nghĩa và dễ hiểu](#sử-dụng-tên-biến-có-ý-nghĩa-và-dễ-hiểu)
     * [Sử dụng cùng từ vựng cho cùng một loại biến](#sử-dụng-cùng-từ-vựng-cho-cùng-một-loại-biến)
     * [Đặt tên sao cho dễ tìm kiếm (phần 1)](#Đặt-tên-sao-cho-dễ-tìm-kiếm-phần-1)
     * [Đặt tên sao cho dễ tìm kiếm (phần 2)](#Đặt-tên-sao-cho-dễ-tìm-kiếm-phần-2)
     * [Đặt tên biến có dễ hiểu](#đặt-tên-biến-dễ-hiểu)
     * [Tránh lồng (nesting) quá nhiều và nên return sớm (phần 1)](#tránh-lồng-nesting-quá-nhiều-và-nên-return-sớm-phần-1)
     * [Tránh lồng (nesting) quá nhiều và nên return sớm (phần 2)](#tránh-lồng-nesting-quá-nhiều-và-nên-return-sớm-phần-2)
     * [Tránh hack não người đọc](#tránh-hack-não-người-đọc)
     * [Đừng thêm những nội dung không cần thiết](#Đừng-thêm-những-nội-dung-không-cần-thiết)
     * [Sử dụng đối số mặc định thay vì phải kiểm tra bằng biểu thức điều kiện](#sử-dụng-đối-số-mặc-định-thay-vì-phải-kiểm-tra-bằng-biểu-thức-điều-kiện)
  3. [So sánh](#so-sánh)
     * [Sử dụng identical comparison](#sử-dụng-identical-comparison)
  4. [Hàm](#hàm)
     * [Đối số của hàm (ít hơn hoặc bằng 2 là lý tưởng)](#Đối-số-của-hàm-ít-hơn-hoặc-bằng-2-là-lý-tưởng)
     * [Hàm chỉ thực hiện một chức năng](#hàm-chỉ-thực-hiện-một-chức-năng)
     * [Tên hàm nên thể hiện chức năng của hàm](#tên-hàm-nên-thể-hiện-chức-năng-của-hàm)
     * [Hàm chỉ nên chứa một cấp trừu tượng](#hàm-chỉ-nên-chứa-một-cấp-trừu-tượng)
     * [Đừng sử dụng cờ như là một đối số của hàm](#Đừng-sử-dụng-cờ-như-là-một-đối-số-của-hàm)
     * [Tránh tác dụng phụ](#tránh-tác-dụng-phụ)
     * [Đừng viết hàm global](#Đừng-viết-hàm-global)
     * [Đừng sử dụng Singleton pattern](#Đừng-sử-dụng-singleton-pattern)
     * [Đóng gói điều kiện](#Đóng-gói-điều-kiện)
     * [Tránh điều kiện phủ định](#tránh-điều-kiện-phủ-định)
     * [Tránh dùng điều kiện](#tránh-dùng-điều-kiện)
     * [Tránh kiểm tra kiểu dữ liệu (phần 1)](#tránh-kiểm-tra-kiểu-dữ-liệu-phần-1)
     * [Tránh kiểm tra kiểu dữ liệu (phần 2)](#tránh-kiểm-tra-kiểu-dữ-liệu-phần-2)
     * [Xóa dead code](#xóa-dead-code)
  5. [Đối tượng và kiến trúc dữ liệu](#Đối-tượng-và-kiến-trúc-dữ-liệu)
     * [Sử dụng đối tượng đóng gói](#sử-dụng-đối-tượng-đóng-gói)
     * [Tạo đối tượng có chứa thuộc tính hoặc phương thức private/protected](#tạo-đối-tượng-có-chứa-thuộc-tính-hoặc-phương-thức-private/protected)
  6. [Lớp](#lớp)
     * [Ưu tiên thành phần hơn kế thừa](#Ưu-tiên-thành-phần-hơn-kế-thừa)
     * [Tránh viết fluent interfaces](#tránh-viết-fluent-interfaces)
  7. [SOLID](#solid)
     * [Nguyên lý trách nhiệm duy nhất (SRP)](#nguyên-lý-trách-nhiệm-duy-nhất-srp)
     * [Nguyên lý Đóng/Mở (OCP)](#nguyên-lý-đóng/mở-ocp)
     * [Nguyên lý thay thế Liskov (LSP)](#nguyên-lý-thay-thế-liskov-lsp)
     * [Nguyên lý phân tách interface (ISP)](#nguyên-lý-phân-tách-interface-isp)
     * [Nguyên lý đảo ngược dependencies (DIP)](#nguyên-lý-đảo-ngược-dependencies-dip)
  8. [Nguyên lý đừng lặp lại chính mình (DRY)](#nguyên-lý-đừng-lặp-lại-chính-mình-dry)
  9. [Các ngôn ngữ khác](#các-ngôn-ngữ-khác)

## Giới thiệu

Đây là những nguyên lý kỹ thuật phần mềm, được trích từ cuốn sách [*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882) của tác giả Robert C. Martin(thường gọi là Uncle Bob) rất thích hợp cho ngôn ngữ PHP. Tài liệu này không phải là sách hướng dẫn về phong cách viết code, mà là hướng dẫn cách làm thế nào để viết phần mềm dễ đọc, dễ sử dụng lại, và dễ cải tiến trong PHP.

Bạn không cần phải tuân theo tất cả các nguyên tắc trong tài liệu này.
Đây chỉ đơn giản là những hướng dẫn, nhưng dù sao nó cũng là đúc kết từ nhiều năm kinh nghiệm của tác giả.

Repository này lấy cảm hứng từ [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript)

Lưu ý: Dù nhiều lập trình viên còn sử dụng PHP 5, nhưng nhiều ví dụ trong đây chỉ chạy được trên PHP 7.1+.

## Biến

### Sử dụng tên biến có ý nghĩa và dễ hiểu

**Chưa tốt:**

```php
$ymdstr = $moment->format('y-m-d');
```

**Tốt:**

```php
$currentDate = $moment->format('y-m-d');
```

**[⬆ Về mục lục](#mục-lục)**

### Sử dụng cùng từ vựng cho cùng một loại biến

**Chưa tốt:**

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

**Tốt:**

```php
getUser();
```

**[⬆ Về mục lục](#mục-lục)**

### Đặt tên sao cho dễ tìm kiếm (phần 1)

Thường thì chúng ta sẽ đọc code nhiều hơn viết code. Nên điều quan trọng là code chúng ta viết ra phải dễ đọc và dễ tìm kiếm.
Nếu *không* đặt tên biến có ý nghĩa và làm chương trình dễ hiểu, chúng ta sẽ gây khó cho những lập trình viên khác. Do đó mỗi khi đặt tên biến, hàm thì hãy đặt có ý nghĩa.

**Chưa tốt:**

```php
// Oh man, 448 là cái giề vậy?
$result = $serializer->serialize($data, 448);
```

**Tốt:**

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

### Đặt tên sao cho dễ tìm kiếm (phần 2)

**Chưa tốt:**

```php
// Lại nữa, 4 nghĩa là cái giề đây?
if ($user->access & 4) {
    // ...
}
```

**Tốt:**

```php
class User
{
    const ACCESS_READ = 1;
    const ACCESS_CREATE = 2;
    const ACCESS_UPDATE = 4;
    const ACCESS_DELETE = 8;
}

if ($user->access & User::ACCESS_UPDATE) {
    // do edit ...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Đặt tên biến dễ hiểu

Tức là đặt tên biến sao cho đọc vô là hiểu nó là gì và nó dùng để làm gì. Không cần phải suy nghĩ, suy diễn.

**Chưa tốt:**

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```

**Không tệ lắm:**

Tốt hơn một chút, nhưng vẫn còn phụ thuộc nhiều vào regex.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

**Tốt:**

Đã giảm phụ thuộc vào regex bằng "naming subpatterns".

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh lồng (nesting) quá nhiều và nên return sớm (phần 1)

Quá nhiều if else lồng nhau sẽ khiến code tăng độ phức tạp, khó debug. Giảm sự phức tạp bằng cách giảm số if else lồng nhau xuống ít nhất có thể. Return sớm chính là một cách giảm số lần lồng nhau.

**Chưa tốt:**

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    } else {
        return false;
    }
}
```

**Tốt:**

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = [
        'friday', 'saturday', 'sunday'
    ];

    return in_array(strtolower($day), $openingDays, true);
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh lồng (nesting) quá nhiều và nên return sớm (phần 2)

**Chưa tốt:**

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            } else {
                return 1;
            }
        } else {
            return 0;
        }
    } else {
        return 'Not supported';
    }
}
```

**Tốt:**

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n > 50) {
        throw new \Exception('Not supported');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh hack não người đọc

Đừng khiến người đọc code phải khó khăn để hiểu ý nghĩa của biến. Tên biến càng rõ ràng càng tốt.

**Chưa tốt:**

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // Đợi đã, `$li` là cái gì?
    dispatch($li);
}
```

**Tốt:**

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```

**[⬆ Về mục lục](#mục-lục)**

### Đừng thêm những nội dung không cần thiết

Nếu tên của class/object đã rõ ràng, không nên lặp lại chúng trong tên biến.

**Chưa tốt:**

```php
class Car
{
    public $carMake;
    public $carModel;
    public $carColor;

    //...
}
```

**Tốt:**

```php
class Car
{
    public $make;
    public $model;
    public $color;

    //...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Sử dụng đối số mặc định thay vì phải kiểm tra bằng biểu thức điều kiện

**Chưa tốt:**

Chưa tốt vì `$breweryName` có thể bị `NULL`.

```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**Không tệ lắm:**

Cái này tốt hơn cái trước, nhưng nó nên quản lý được giá trị của biến thì tốt hơn.

```php
function createMicrobrewery($name = null): void
{
    $breweryName = $name ?: 'Hipster Brew Co.';
    // ...
}
```

**Tốt:**

 Bạn có thể sử dụng [type hinting](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration) và chắc chắn `$breweryName` sẽ không bị `NULL`.

```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**[⬆ Về mục lục](#mục-lục)**

## So sánh

**[⬆ Về mục lục](#mục-lục)**

### Sử dụng [identical comparison](http://php.net/manual/en/language.operators.comparison.php)

**Chưa tốt:**

Sử dụng *simple comparison* (so sánh đơn giản)

```php
$a = '42';
$b = 42;
Sử dụng simple comparison thì nó sẽ tự chuyển kiểu string qua kiểu int

if ($a != $b) {
   //Biểu thức này sẽ trả về `false`
}

```
Phép so sánh $a != $b trả về `false` nhưng trong thực tế thì nó phải là `true`.
**Chuỗi** '42' thì phải khác **số** 42 chứ đúng không.

**Tốt:**

Sử dụng *identical comparison* (so sánh giống hệt nhau) để so sánh cả kiểu dữ liệu và giá trị

```php
if ($a !== $b) {
    //Biểu thức này trả về `true`
}

```


**[⬆ Về mục lục](#mục-lục)**


## Hàm

### Đối số của hàm (ít hơn hoặc bằng 2 là lý tưởng)

Giới hạn số lượng đối số (parameters) của hàm vô cùng quan trọng bởi vì nó giúp dễ test hơn.
Có nhiều hơn 3 đối số dẫn đến một tổ hợp rất nhiều trường hợp khác nhau cần phải test.

Lý tưởng nhất là khi hàm không có đối số nào. Một hoặc hai đối số là ok, còn ba thì nên hạn chế.
Bất cứ khi nào hàm có nhiều hơn 3 đối số thì cần phải xem xét tìm cách giảm bớt lại.
Bởi vì nếu hàm có nhiều hơn hai đối số thì nó phải xử lý rất nhiều.

**Chưa tốt:**

```php
function createMenu(string $title, string $body, string $buttonText, bool $cancellable): void
{
    // ...
}
```

**Tốt:**

```php
class MenuConfig
{
    public $title;
    public $body;
    public $buttonText;
    public $cancellable = false;
}

$config = new MenuConfig();
$config->title = 'Foo';
$config->body = 'Bar';
$config->buttonText = 'Baz';
$config->cancellable = true;

function createMenu(MenuConfig $config): void
{
    // ...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Hàm chỉ thực hiện một chức năng

Đây là nguyên tắc quan trọng nhất trong phát triển phần mềm.
Khi hàm thực hiện nhiều hơn một chức năng, chúng khó biên dịch, kiểm tra và biết được nguyên nhân lỗi.
Khi bạn tạo hàm chỉ với một chức năng, sẽ dễ dàng refactor hơn và code sẽ dễ đọc hơn.
Nếu làm được điều này thì bạn sẽ tốt hơn nhiều lập trình viên khác.

**Chưa tốt:**
```php
function emailClients(array $clients): void
{
    foreach ($clients as $client) {
        $clientRecord = $db->find($client);
        if ($clientRecord->isActive()) {
            email($client);
        }
    }
}
```

**Tốt:**

```php
function emailClients(array $clients): void
{
    $activeClients = activeClients($clients);
    array_walk($activeClients, 'email');
}

function activeClients(array $clients): array
{
    return array_filter($clients, 'isClientActive');
}

function isClientActive(int $client): bool
{
    $clientRecord = $db->find($client);

    return $clientRecord->isActive();
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tên hàm nên thể hiện chức năng của hàm

**Chưa tốt:**

```php
class Email
{
    //...

    public function handle(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// Hàm này dùng làm gì? Có phải nó xử lý mail? Nó có đang ghi gì vào file không?
$message->handle();
```

**Tốt:**

```php
class Email 
{
    //...

    public function send(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// Rõ ràng và minh bạch, hàm này gửi mail
$message->send();
```

**[⬆ Về mục lục](#mục-lục)**

### Hàm chỉ nên có độ trừu tượng một cấp

Khi bạn có độ trừu tượng nhiều hơn một cấp thì hàm thường phải làm quá nhiều việc.
Hãy chia tách hàm ra thành nhiều phần để dễ sử dụng lại và dễ test.

**Chưa tốt:**

```php
function parseBetterJSAlternative(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    $ast = [];
    foreach ($tokens as $token) {
        // lex...
    }

    foreach ($ast as $node) {
        // parse...
    }
}
```

**Cũng chưa tốt:**

Chúng ta đã thực hiện tách ra vài hàm, nhưng hàm `parseBetterJSAlternative()` vẫn còn khá phức tạp và khó test.

```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): array
{
    $ast = [];
    foreach ($tokens as $token) {
        $ast[] = /* ... */;
    }

    return $ast;
}

function parseBetterJSAlternative(string $code): void
{
    $tokens = tokenize($code);
    $ast = lexer($tokens);
    foreach ($ast as $node) {
        // parse...
    }
}
```

**Tốt:**

Giải pháp tốt nhất là chuyển các phần thành các dependencies của hàm `parseBetterJSAlternative()`

```php
class Tokenizer
{
    public function tokenize(string $code): array
    {
        $regexes = [
            // ...
        ];

        $statements = explode(' ', $code);
        $tokens = [];
        foreach ($regexes as $regex) {
            foreach ($statements as $statement) {
                $tokens[] = /* ... */;
            }
        }

        return $tokens;
    }
}

class Lexer
{
    public function lexify(array $tokens): array
    {
        $ast = [];
        foreach ($tokens as $token) {
            $ast[] = /* ... */;
        }

        return $ast;
    }
}

class BetterJSAlternative
{
    private $tokenizer;
    private $lexer;

    public function __construct(Tokenizer $tokenizer, Lexer $lexer)
    {
        $this->tokenizer = $tokenizer;
        $this->lexer = $lexer;
    }

    public function parse(string $code): void
    {
        $tokens = $this->tokenizer->tokenize($code);
        $ast = $this->lexer->lexify($tokens);
        foreach ($ast as $node) {
            // parse...
        }
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

### Đừng sử dụng cờ như là một đối số của hàm

Cờ dùng để nói rằng hàm này thực hiện nhiều hơn một công việc. Nhưng hàm thì chỉ nên xử lý một công việc mà thôi.
Do đó hãy chia tách hàm của bạn nếu như chúng có nhiều luồng code phân biệt bằng boolean(true/false).

**Chưa tốt:**

```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/'.$name);
    } else {
        touch($name);
    }
}
```

**Tốt:**

```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/'.$name);
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh tác dụng phụ

Một hàm sinh ra tác dụng phụ nếu nó thực hiện thêm việc khác ngoài việc lấy giá trị vào và trả về một hoặc nhiều giá trị khác.
Tác dụng phụ có thể là viết vào một file nào đó, sửa đổi biến global, hoặc vô tình chuyển hết tiền của bạn cho người lạ nào đó.

Vậy nếu bây giờ bạn cần hàm thực hiện các tác dụng phụ đó thì sao. Giống như ví dụ trước, bạn cần ghi vào file. Điều bạn cần làm
là tập trung những việc này lại một chỗ. Đừng viết vài hàm và vài lớp chỉ để ghi vào vài file cụ thể.
Hãy viết một service để làm điều đó. Một và chỉ một service.

Hãy tránh những sai lầm phổ biến như: chia sẻ trạng thái giữa các object mà không tuân theo cấu trúc nào,
sử dụng kiểu dữ liệu có thể thay đổi/bị thay đổi dễ dàng, không tổng hợp các tác dụng phụ có thể xảy ra khi viết hàm.

**Chưa tốt:**

```php
// Biến glabal được tham chiếu bởi hàm bên dưới.
// Nếu ta tạo một function khác sử dụng chính biến name, ví dụ bên dưới cho thấy nó biến thành array và đã bị phá vỡ.
$name = 'Ryan McDermott';

function splitIntoFirstAndLastName(): void
{
    global $name;

    $name = explode(' ', $name);
}

splitIntoFirstAndLastName();

var_dump($name); // ['Ryan', 'McDermott'];
```

**Tốt:**

```php
function splitIntoFirstAndLastName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitIntoFirstAndLastName($name);

var_dump($name); // 'Ryan McDermott';
var_dump($newName); // ['Ryan', 'McDermott'];
```

**[⬆ Về mục lục](#mục-lục)**

### Đừng viết hàm global

Dùng nhiều hàm global là bad practice với nhiều ngôn ngữ bởi vì có thể gây xung đột với thư viện khác 
và người sử dụng API của bạn không hề hay biết gì cho đến khi nhận được thông báo lỗi.

Hãy xem xét ví dụ sau: bạn sẽ làm gì nếu muốn trả về một mảng.

Bạn có thể viết hàm global như `config()`, nhưng nó có thể xung đột với thư viện khác thực hiện cùng chức năng.

**Chưa tốt:**

```php
function config(): array
{
    return  [
        'foo' => 'bar',
    ]
}
```

**Tốt:**

```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        return isset($this->configuration[$key]) ? $this->configuration[$key] : null;
    }
}
```

Tạo instance của lớp `Configuration` 

```php
$configuration = new Configuration([
    'foo' => 'bar',
]);
```

Và bây giờ sử dụng instance `Configuration` trong ứng dụng của bạn.

**[⬆ Về mục lục](#mục-lục)**

### Đừng sử dụng Singleton pattern

Singleton là một [anti-pattern](https://en.wikipedia.org/wiki/Singleton_pattern). Trích đoạn từ Brian Button:
 1. Chúng thường được sử dụng như **global instance**, vì sao lại Chưa tốt? Bởi vì **bạn ẩn dependencies** của ứng dụng bên trong code của bạn,
  thay vì thông qua interfaces
 2. Chúng vi phạm [single responsibility principle](#single-responsibility-principle-srp): bởi vì thực tế là **chúng điều khiển những gì chúng tạo ra và vòng đời của nó**
 3. Chúng đã tạo ra kiểu code [coupling](https://en.wikipedia.org/wiki/Coupling_%28computer_programming%29). Đây là một sự giả mạo và được giấu bằng cách tạo ra nhiều trường hợp **test khó khăn hơn**.
 4. Chúng giữ trạng thái suốt vòng đời của ứng dụng. Bạn nên kết thúc sớm testing khi lỗi. Nhưng Singleton thì lại duy trì trạng thái nên nó Chưa tốt.

Đây là một ý kiến khác của [Misko Hevery](http://misko.hevery.com/about/) về [gốc rễ của vấn đề](http://misko.hevery.com/2008/08/25/root-cause-of-singletons/).

**Chưa tốt:**

```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): DBConnection
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

**Tốt:**

```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

     // ...
}
```

Tạo instance của lớp `DBConnection` và cấu hình chúng với [DSN](http://php.net/manual/en/pdo.construct.php#refsect1-pdo.construct-parameters).

```php
$connection = new DBConnection($dsn);
```

Và bây giờ sử dụng instance `DBConnection` cho ứng dụng của bạn.

**[⬆ Về mục lục](#mục-lục)**

### Đóng gói điều kiện

**Chưa tốt:**

```php
if ($article->state === 'published') {
    // ...
}
```

**Tốt:**

```php
if ($article->isPublished()) {
    // ...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh điều kiện phủ định

**Chưa tốt:**

```php
function isDOMNodeNotPresent(\DOMNode $node): bool
{
    // ...
}

if (!isDOMNodeNotPresent($node))
{
    // ...
}
```

**Tốt:**

```php
function isDOMNodePresent(\DOMNode $node): bool
{
    // ...
}

if (isDOMNodePresent($node)) {
    // ...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh dùng điều kiện

Điều này có vẻ không khả quan. Hầu hết mọi người sẽ thắc mắc,
"làm sao có thể làm gì đó mà không có `if`?" Bạn có thể dùng tính đa hình để hoàn thành việc đó trong khá nhiều trường hợp.
Câu hỏi thứ hai là, "ồ ngon nhưng tại sao phải làm thế?"
Bởi vì khái niệm clean code mà ta đã học trước đây: một hàm chỉ nên thực hiện một chức năng.
Khi bạn có một lớp hoặc hàm chứa `if`, tức là bạn đang muốn nó thực hiện nhiều việc. Luôn nhớ, chỉ một mà thôi.

**Chưa tốt:**

```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

**Tốt:**

```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh kiểm tra kiểu dữ liệu (phần 1)

PHP là một ngôn ngữ không ràng buộc kiểu dữ liệu, nghĩa hàm có thể nhận bất kỳ kiểu nào.
Thỉnh thoảng thì chúng ta bị ảnh hưởng bởi sự tự do này và nó trở thành điều kiện để phải kiểm tra kiểu dữ liệu trong hàm.
Có nhiều cách để tránh phải làm việc đó.

Điều đầu tiên cần làm là tạo ra những API nhất quán.

**Chưa tốt:**

```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedalTo(new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->driveTo(new Location('texas'));
    }
}
```

**Tốt:**

```php
function travelToTexas(Traveler $vehicle): void
{
    $vehicle->travelTo(new Location('texas'));
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh kiểm tra kiểu dữ liệu (phần 2)

Nếu bạn đang làm việc với các kiểu dữ liệu nguyên thủy như strings, integers, và arrays,
và sử dụng PHP 7+ và bạn không thể sử dụng tính đa hình nhưng bạn vẫn cảm thấy cần kiểm tra kiểu dữ liệu, hãy xem
[type declaration](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)
hoặc strict mode. Nó cung cấp cho bạn kiểu static trên PHP standard.
Vấn đề thông thường khi kiểm tra kiểu dữ liệu là sẽ khiến code khó đọc nên tóm lại mất nhiều hơn là được.

Hãy giữ PHP nguyên thủy, viết tests cho tốt, và code reviews cẩn thận là được.
Nếu không thì chỉ còn cách định nghĩa theo kiểu nghiêm ngặt(strict type declaration) hoặc dùng strict mode.

**Chưa tốt:**

```php
function combine($val1, $val2): int
{
    if (!is_numeric($val1) || !is_numeric($val2)) {
        throw new \Exception('Must be of type Number');
    }

    return $val1 + $val2;
}
```

**Tốt:**

```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ Về mục lục](#mục-lục)**

### Xóa dead code

Dead code thì cũng củ chuối giống như duplicate code. Không có lý do gì để giữ chúng.
Nếu đoạn code nào đó không được gọi, hãy xóa đi!
Sau này cần thì chỉ cần tìm lại phiên bản trước bằng git là được.

**Chưa tốt:**

```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**Tốt:**

```php
function requestModule(string $url): void
{
    // ...
}

$request = requestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**[⬆ Về mục lục](#mục-lục)**


## Đối tượng và kiến trúc dữ liệu

### Sử dụng đối tượng đóng gói

Trong PHP bạn có thể khai `public`, `protected` và `private` cho phương thức và thuộc tính.
Hãy sử dụng chúng để kiểm soát được sự thay đổi thuộc tính trong object.

* Khi bạn muốn nhiều hơn là chỉ nhận được thuộc tính của object,
thì ưu điểm là ta không cần phải tìm kiếm và thay đổi quyền mỗi khi truy cập vào object.
* Giúp tạo validation đơn giản mỗi khi thực hiện `set`.
* Đóng gói các thành phần bên trong.
* Dễ dàng ghi log và xử lý lỗi khi get và set.
* Kế thừa lớp, bạn có thể ghi đè những phương thức mặc định.
* Bạn có thể lazy load các thuộc tính của object, giả sử nó được lấy từ máy chủ chẳng hạn.

Thêm vào đó, đây là một phần của nguyên tắc [Open/Closed](#openclosed-principle-ocp).

**Chưa tốt:**

```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->balance -= 100;
```

**Tốt:**

```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
      $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Amount greater than available balance.');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->withdraw($shoesPrice);

// Get balance
$balance = $bankAccount->getBalance();
```

**[⬆ Về mục lục](#mục-lục)**

### Tạo đối tượng có chứa thuộc tính hoặc phương thức private/protected

* Phương thức và thuộc tính `public` khá nguy hiểm, bởi vì vài dòng code phía 
bên ngoài có thể dễ dàng thay đổi chúng và bạn không thể kiểm soát được nó bị
thay đổi những gì. **Thay đổi trong một lớp thì nguy hiểm cho tất cả các người dùng của lớp đó.**
* `protected` cũng nguy hiểm không kém, bởi vì chúng được cấp quyền ở tất cả các lớp con. Điều này có nghĩa là sự khác nhau giữa public và protected chỉ là cơ chế truy cập, nhưng tính đóng gói đảm bảo vẫn giữ nguyên. **Sửa đổi trong lớp thì rất nguy hiểm cho các lớp con.**
* `private` sửa đổi đảm bảo rằng code **sửa đổi chỉ nguy hiểm trong lớp đó** (bạn sẽ được an toàn khi sửa và không có hiệu ứng [Jenga](http://www.urbandictionary.com/define.php?term=Jengaphobia&defid=2494196)).

Do đó, hãy mặc định sử dụng `private` và `public/protected` khi bạn cần cung cấp sự truy cập cho các class bên ngoài.

Đọc thêm tại [blog post](http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html) được viết bởi [Fabien Potencier](https://github.com/fabpot).

**Chưa tốt:**

```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->name; // Employee name: John Doe
```

**Tốt:**

```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->getName(); // Employee name: John Doe
```

**[⬆ Về mục lục](#mục-lục)**

## Lớp

### Ưu tiên thành phần hơn kế thừa

Như đã nói trong [*Design Patterns*](https://en.wikipedia.org/wiki/Design_Patterns) nổi tiếng của Gang of Four,
bạn nên ưu tiên sử dụng "kiểu thành phần" hơn là "kiểu kế thừa". Có nhiều lý do để sử dụng kiểu kế thừa và cũng có nhiều nguyên nhân để sử dụng kiểu thành phần.
Điểm chính của sự tối đa hóa này là nếu bạn thích theo kiểu kế thừa,
hãy thử suy nghĩ "kiểu thành phần" có thể giúp giải quyết vấn đề tốt hơn không. Vì có một vài trường hợp nó sẽ tốt hơn.

Có thể bạn sẽ tự hỏi, "khi nào thì nên dùng kế thừa?" Nó tùy thuộc vào từng vấn đề, khi nào thì kiểu kế thừa tốt hơn kiểu thành phần:

1. Kiểu kế thừa đó đại diện cho một mối quan hệ "is-a" (Ví dụ: Người->Động vật) chứ không phải mối quan hệ "has-a" (Người dùng->Thông tin người dùng).
2. Bạn cần sử dụng lại code từ lớp cha (Người có thể di chuyển như động vật).
3. Bạn muốn khi sửa đổi lớp cha thì tất cả lớp có liên quan sẽ thay đổi dễ dàng.
(Thay đổi lượng calo của tất cả động vật khi chúng di chuyển).

**Chưa tốt:**

```php
class Employee 
{
    private $name;
    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// Chưa tốt vì Employees "có" thuế. 
// EmployeeTaxData không phải là một loại của Employee

class EmployeeTaxData extends Employee 
{
    private $ssn;
    private $salary;
    
    public function __construct(string $name, string $email, string $ssn, string $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

**Tốt:**

```php
class EmployeeTaxData 
{
    private $ssn;
    private $salary;

    public function __construct(string $ssn, string $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee 
{
    private $name;
    private $email;
    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(string $ssn, string $salary)
    {
        $this->taxData = new EmployeeTaxData($ssn, $salary);
    }

    // ...
}
```

**[⬆ Về mục lục](#mục-lục)**

### Tránh viết fluent interfaces

[Fluent interface](https://en.wikipedia.org/wiki/Fluent_interface) là một API hướng đối tượng có mục đích cải thiện tính dễ đọc của source code bằng cách
sử dụng [Method chaining](https://en.wikipedia.org/wiki/Method_chaining).

Trong một số ngữ cảnh, thường là khi xây dựng object nơi mà pattern này giảm tính rườm rà của code (ví dụ [PHPUnit Mock Builder](https://phpunit.de/manual/current/en/test-doubles.html)
hoặc [Doctrine Query Builder](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html)),
sẽ gây ra một số thiệt hại như sau:

1. Phá vỡ [Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_%28object-oriented_programming%29)
2. Phá vỡ [Decorators](https://en.wikipedia.org/wiki/Decorator_pattern)
3. Khó tạo [mock](https://en.wikipedia.org/wiki/Mock_object) hơn trong test suite
4. Khiến cho khó đọc "sự khác nhau giữa các file" hơn khi commit code

Để biết thêm thông tin chi tiết, vui lòng đọc [bài viết](https://ocramius.github.io/blog/fluent-interfaces-are-evil/)
được viết bởi [Marco Pivetta](https://github.com/Ocramius).

**Chưa tốt:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): self
    {
        $this->make = $make;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
  ->setColor('pink')
  ->setMake('Ford')
  ->setModel('F-150')
  ->dump();
```

**Tốt:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): void
    {
        $this->make = $make;
    }

    public function setModel(string $model): void
    {
        $this->model = $model;
    }

    public function setColor(string $color): void
    {
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car();
$car->setColor('pink');
$car->setMake('Ford');
$car->setModel('F-150');
$car->dump();
```

**[⬆ Về mục lục](#mục-lục)**

## SOLID

**SOLID** là từ viết tắt được đưa ra bởi Michael Feathers cho 5 nguyên lý đầu tiên của Robert Martin, 5 nguyên tắc cơ bản của lập trình hướng đối tượng.

 * [S: Nguyên lý trách nhiệm duy nhất (SRP)](#single-responsibility-principle-srp)
 * [O: Nguyên lý Đóng/Mở (OCP)](#openclosed-principle-ocp)
 * [L: Nguyên lý thay thế Liskov (LSP)](#liskov-substitution-principle-lsp)
 * [I: Nguyên lý phân tách interface (ISP)](#interface-segregation-principle-isp)
 * [D: Nguyên lý đảo ngược dependencies (DIP)](#dependency-inversion-principle-dip)

### Nguyên lý trách nhiệm duy nhất (SRP)

Như đã đề cập trong cuốn Clean Code, "Không nên có nhiều hơn một lý do để thay đổi class".
Viết một class với thật nhiều chức năng thì quá sướng. Vấn đề là class không có khái niệm liên kết và nó có khá nhiều lý do để thay đổi.
Nếu quá nhiều chức năng trong một class thì khi thay đổi gì đó mình không biết được hết những ảnh hưởng của nó đến các chức năng khác trong các module liên quan.

**Chưa tốt:**

```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

**Tốt:**

```php
class UserAuth 
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }
    
    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings 
{
    private $user;
    private $auth;

    public function __construct(User $user) 
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

### Nguyên lý Đóng/Mở (OCP)

Như đã đề cập bởi Bertrand Meyer, "thực thể phần mềm (lớp, modules, hàm,
etc...) nên cho phép mở rộng, nhưng không cho phép sửa đổi." Điều đó có nghĩa là gì? Nguyên lý này đơn giản là nên cho phép người dùng
thêm mới mà không được thay đổi code hiện tại.

**Chưa tốt:**

```php
abstract class Adapter
{
    protected $name;

    public function getName(): string
    {
        return $this->name;
    }
}

class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        $adapterName = $this->adapter->getName();

        if ($adapterName === 'ajaxAdapter') {
            return $this->makeAjaxCall($url);
        } elseif ($adapterName === 'httpNodeAdapter') {
            return $this->makeHttpCall($url);
        }
    }

    private function makeAjaxCall(string $url): Promise
    {
        // request and return promise
    }

    private function makeHttpCall(string $url): Promise
    {
        // request and return promise
    }
}
```

**Tốt:**

```php
interface Adapter
{
    public function request(string $url): Promise;
}

class AjaxAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        return $this->adapter->request($url);
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

### Nguyên lý thay thế Liskov (LSP)

Nguyên lý này được định nghĩa như sau "Nếu S là phụ thuộc của T, thì object của T có thể **được thay thế** bởi object của S
(nghĩa là object của S có thể thay thế object của T) mà không làm thay đổi các thuộc tính của chương trình(tính đúng đắn, công việc thực hiện,...)"

Để dễ hiểu hơn, nếu bạn có một class cha và một class con,
sau đó class cha và class con có thể được sử dụng hoán đổi cho nhau mà không sai kết quả trả về.
Có thể vẫn còn khó hiểu, hãy xem ví dụ cơ bản Square-Rectangle bên dưới.

Trong toán học, hình vuông là hình chữ nhật, nhưng nếu bạn sử dụng quan hệ "is-a" qua kế thừa, bạn sẽ gặp rắc rối.

**Chưa tốt:**

```php
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function render(int $area): void
    {
        // ...
    }

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $rectangle->setWidth(4);
        $rectangle->setHeight(5);
        $area = $rectangle->getArea(); // Lỗi rồi: Đoạn này sẽ trả về 25, nhưng 20 mới là kết quả đúng.
        $rectangle->render($area);
    }
}

$rectangles = [new Rectangle(), new Rectangle(), new Square()];
renderLargeRectangles($rectangles);
```

**Tốt:**

```php
abstract class Shape
{
    abstract public function getArea(): int;

    public function render(int $area): void
    {
        // ...
    }
}

class Rectangle extends Shape
{
    private $width;
    private $height;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Shape
{
    private $length;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return pow($this->length, 2);
    }
}

/**
 * @param Rectangle[] $rectangles
 */
function renderLargeRectangles(array $rectangles): void
{
    foreach ($rectangles as $rectangle) {
        $area = $rectangle->getArea(); 
        $rectangle->render($area);
    }
}

$shapes = [new Rectangle(4, 5), new Rectangle(4, 5), new Square(5)];
renderLargeRectangles($shapes);
```

**[⬆ Về mục lục](#mục-lục)**

### Nguyên lý phân tách interface (ISP)

ISP đề cập rằng "Không nên ép người dùng phải phụ thuộc vào interface mà họ không sử dụng."

Để hiểu ý nghĩa của nguyên tắc này, hãy nhìn vào những class yêu cầu một số lượng lớn các object cần phải inject vào để sử dụng.
Không yêu cầu người dùng phải inject số lượng lớn các tùy chọn là một lợi thế, bởi vì hầu hết chúng không cần thiết.
Hãy coi chúng là tùy chọn(có thể không dùng) để giúp cho interface bớt phình to.

**Chưa tốt:**

```php
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        // ...... eating in lunch break
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }

    public function eat(): void
    {
        //.... robot can't eat, but it must implement this method
    }
}
```

**Tốt:**

Không phải tất cả worker đều là employee, nhưng employee là một worker.

```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        //.... eating in lunch break
    }
}

// robot can only work
class Robot implements Workable
{
    public function work(): void
    {
        // ....working
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

### Nguyên lý đảo ngược dependencies (DIP)

Nguyên lý này đề cập 2 vấn đề cơ bản:
1. Module cấp cao không nên phụ thuộc vào module cấp thấp. Cả hai nên phụ thuộc vào abstract.
2. Abstract không nên phụ thuộc vào chi tiết, mà phải ngược lại.

Hơi khó hiểu một chút đúng không? Nhưng nếu bạn làm việc với PHP frameworks (ví dụ Symfony), bạn sẽ thấy nguyên tắc này được áp dụng trên Dependency
Injection(DI). Một lợi ích lớn của việc này là chúng giảm sự trùng lặp giữa các modules. Trùng lặp thì tất nhiên Chưa tốt vì
chúng khiến code khó refactor.

**Chưa tốt:**

```php
class Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**Tốt:**

```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

## Nguyên lý đừng lặp lại chính mình (DRY)

Đọc hiểu về nguyên lý [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

Tốt nhất nên chống lặp code ngay khi có thể. Vì lặp code không tốt tí nào, khi bạn muốn thay đổi logic bạn cần phải sửa nhiều chỗ.

Hãy tưởng tượng bạn đang vận hành một nhà hàng và bạn theo dõi lượng hàng tồn kho của bạn: cà chua, hành, tỏi, gia vị,...
Nếu bạn có nhiều danh sách để quản lý chúng, bạn cần cập nhật tất cả các danh sách đó mỗi khi bạn bán một đĩa thức ăn.
Nhưng nếu như bạn chỉ có 1 danh sách, thì chỉ cần cập nhật ở một nơi!

Thỉnh thoảng vẫn có lặp code bởi vì bạn có hai hoặc nhiều hơn những thứ khác nhau, có nhiều điểm chung, nhưng sự khác nhau 
giữa chúng buộc bạn phải chia ra 2 hàm làm rất nhiều việc.
Để xóa bỏ lặp code, cần tạo ra một abstract có thể xử lý sự khác biệt giữa chúng với chỉ 1 hàm/module/lớp.

Tạo ra được abstract tốt rất quan trọng và khó, đó là lý do tại sao bạn nên dựa theo các nguyên lý [SOLID](#solid) được đưa ra tại mục [Lớp](#lớp).
Abstract củ chuối có thể sẽ tệ hại hơn là lặp code, hãy cẩn thận!
Nếu có thể tạo một abstract tốt, hãy tạo nó! Đừng lặp lại code, nếu không bạn sẽ phải rất cực khổ mỗi khi muốn sửa đổi gì đó.

**Chưa tốt:**

```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**Tốt:**

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        $expectedSalary = $employee->calculateExpectedSalary();
        $experience = $employee->getExperience();
        $githubLink = $employee->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**Rất tốt:**

Sử dụng một phiên bản gọn hơn

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([
            $employee->calculateExpectedSalary(),
            $employee->getExperience(),
            $employee->getGithubLink()
        ]);
    }
}
```

**[⬆ Về mục lục](#mục-lục)**

## Các ngôn ngữ khác

* :cn: **Trung Quốc:**
   * [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
* :ru: **Nga:**
   * [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
* :es: **Tây Ban Nha:**
   * [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
* :brazil: **Bồ Đào Nha:**
   * [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
   * [jeanjar/clean-code-php](https://github.com/jeanjar/clean-code-php/tree/pt-br)
* :thailand: **Thái Lan:**
   * [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
* :fr: **Pháp:**
   * [errorname/clean-code-php](https://github.com/errorname/clean-code-php)

**[⬆ Về mục lục](#mục-lục)**
