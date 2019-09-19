# Example 5

```php
public function calculateTotalPayment(String $code, float $quantity, float unitPrice)
{   
    if ($code[0] === "LCD" || $code[0] === "KB" || $code[0] === "HDD" || $code[0] === "CPU") {
        return $quantity * $unitPrice * (1 + VAT - DISCOUNT_PERCENTAGE);
    } else {
        return $quantity * $unitPrice * (1 + VAT);
    }
}
```
Vi phạm: 
+So sánh quá nhiều trong if
+Sử dụng else
+thực hiện tính toán trong return

 Lời giải:

```php
 public function calculateTotalPayment(String $code, float $quantity, float unitPrice)
{   
    if (isDiscountedCategory($code)) {
        return caculatePaymentWithDiscount($quantity, $unitPrice);
    } else {
        return caculatePayment($quantity, $unitPrice);
    }
}
```