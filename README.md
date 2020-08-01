Test Cases

| Command     | Works |
|-------------|-------|
| a. `./vendor/bin/phpunit --no-configuration` | yes |
| b. `./vendor/bin/phpunit --no-configuration .` | no (2) |
| c. `./vendor/bin/phpunit --no-configuration --filter "/(Project\\TestsTest::(.*) OR Project\\Tests\\SrcTest::(.*))$/" .` | no (1,2) |
| d. `./vendor/bin/phpunit --no-configuration --filter "/(Project\\TestsTest::(.*) OR Project\\Tests\\SrcTest::(.*))$/"` | no (1,3) |
| e. `./vendor/bin/phpunit --configuration phpunit.xml` | yes |
|   |   |
| f. `./vendor/bin/phpunit --configuration phpunit.xml --filter "/(Project\\TestsTest::(.*) OR Project\\Tests\\SrcTest::(.*))$/" .` | no (1,2) |
| g. `./vendor/bin/phpunit --configuration phpunit.xml --filter "/(Project\\TestsTest::(.*) OR Project\\Tests\\SrcTest::(.*))$/"` | yes (1) |

1. Replace ` OR ` with `|`
2. _PHP Fatal error:  Declaration of PharIo\Manifest\ApplicationTest::setUp() must be compatible with PHPUnit\Framework\TestCase::setUp(): void in /Users/user/PhpstormProjects/project/vendor/phar-io/manifest/tests/values/ApplicationTest.php on line 4_
3. Requires directory option, it just shows PHPUnit help

### In conclusion
1. never use project root for loading tests (even with a plain PHPUnit install, vendor will cause trouble)
2. always load tests via XML configuration
3. IDE should be intelligent enough to omit directory option when:
   1. `--filter` is used and;
   2. `--configuration` is used and;
   3. "Alternative patterns base path" is the same as project root path
