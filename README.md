Test Cases

| Command     | Works |
|-------------|-------|
| `./vendor/phpunit/phpunit/phpunit --no-configuration` | yes |
| `./vendor/phpunit/phpunit/phpunit --no-configuration .` | no (1) |
| `./vendor/phpunit/phpunit/phpunit --no-configuration --filter "/(Project\\TestsTest::(.*) OR Project\\Tests\\SrcTest::(.*))$/" .` | no (1) |
| `./vendor/phpunit/phpunit/phpunit --configuration phpunit.xml` | yes |

1. PHP Fatal error:  Declaration of PharIo\Manifest\ApplicationTest::setUp() must be compatible with PHPUnit\Framework\TestCase::setUp(): void in /Users/user/PhpstormProjects/project/vendor/phar-io/manifest/tests/values/ApplicationTest.php on line 4`
