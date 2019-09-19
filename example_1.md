# Viết If Else Quá nhiều

Ví dụ ta có đoạn code:

```php
function isShopOpen($a): bool
{
    if ($a) {
        if (is_string($a)) {
            $a = strtolower($a);
            $ngay = $a;
            if ($ngay === 'friday') {
                return true;
            } elseif ($ngay === 'saturday') {
                return true;
            } elseif ($ngay === 'sunday') {
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

Kết quả sau khi refactor:

```php
function isShopOpen($a): bool
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

Các kĩ thụât sử dụng:

-   Đặt tên biến dễ hiểu.
-   Tránh lồng If-else quá nhiều.
-   Không thêm những nội dung không cần thiết.
