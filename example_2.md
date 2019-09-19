# Hàm chỉ thực hiện một chức năng

```php
function send(array $a): void
{
    foreach ($a as $b) {
        $clientRecord = $db->find($b);
        if ($clientRecord->isActive()) {
            email($client);
        }
    }
}
```

Kết quả khi refactor:

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

Các kĩ thụât sử dụng:

-   Đặt tên biến khó hiểu
-   Tên hàm nên thể hiện chức năng của hàm
-   Hàm chỉ thực hiện một chức năng
