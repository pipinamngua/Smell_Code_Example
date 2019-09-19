# Example 3

```php
class AwesomeAddon {
    private $settings;
    public function __construct( $settings ) {
        $this->set_settings( $settings );
    }
    protected function set_settings( $settings ) {
        if ( ! is_array( $settings ) ) {
            throw new \Exception( 'Invalid settings' );
        }
        
        $this->settings = $settings;
    }
    
    protected function do_something_awesome() {
        //...
    }
}

class EvenMoreAwesomeAddon {
    private $settings;
    public function __construct( $settings ) {
        $this->set_settings( $settings );
    }
    protected function set_settings( $settings ) {
        if ( ! is_array( $settings ) ) {
            throw new \Exception( 'Invalid settings' );
        }
        
        $this->settings = $settings;
    }
    
    protected function do_something_even_more_awesome() {
        //...
    }
}
```

 Đáp án:
 ```php
 <?php
abstract class Addon {
    protected $settings;
    protected function set_settings( $settings ) {
        if ( ! is_array( $settings ) ) {
            throw new \Exception( 'Invalid settings' );
        }
        
        $this->settings = $settings;
    }
}
class AwesomeAddon extends Addon {
    public function __construct( $settings ) {
        $this->set_settings( $settings );
    }
    
    protected function do_something_awesome() {
        //...
    }
}
class EvenMoreAwesomeAddon extends Addon {
    public function __construct( $settings ) {
        $this->set_settings( $settings );
    }
    
    protected function do_something_even_more_awesome() {
        //...
    }
}
```
Code Smell vi phạm
Bị lặp code
vi phạm nguyên lú DRY