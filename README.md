# Disposable email domains filter
[![GitHub version](https://badge.fury.io/gh/purringCatFoundation%2FDisposableEmail.svg)](https://badge.fury.io/gh/purringCatFoundation%2FDisposableEmail) ![](https://travis-ci.org/purringCatFoundation/DisposableEmail.svg?branch=master) [![SensioLabsInsight](https://insight.sensiolabs.com/projects/2006a52e-6bae-4316-bdc8-ebf563fce5ed/mini.png)](https://insight.sensiolabs.com/projects/2006a52e-6bae-4316-bdc8-ebf563fce5ed)

Our domain repositories come from [repository](https://github.com/martenson/disposable-email-domains) licensed by [Public Domain License(CC0 1.0)](https://creativecommons.org/publicdomain/zero/1.0/).
 
Domain repository date: [09.11.2017](https://github.com/martenson/disposable-email-domains/commit/170d0826cae6f793801e6e39fd6eac7e9b314063#diff-45615409a4404da1979f49268dab8286)


This repository is contributed by [MIT License](LICENSE) but files [blocklist.conf](src/Resource/lists/blocklist.conf) and [trustlist.conf](src/Resource/lists/trustlist.conf) are contributed by [Public Domain License(CC0 1.0)](https://creativecommons.org/publicdomain/zero/1.0/).

# Basic Usage

```PHP
<?php

require 'vendor/autoload.php';

use PCF\DisposableEmail\ListedVerifier;
use PCF\DisposableEmail\SimpleDomainCollection;
use PCF\DisposableEmail\Resource\AbstractResourceList;

$collection = new SimpleDomainCollection();
$collection->setBlockedList(AbstractResourceList::getList('block'));
$collection->setTrustedList(AbstractResourceList::getList('trust'));
$collection->setKnownList([
    //Add domains that you know, if you want
]);

$verifier = new ListedVerifier($collection);

$mail = 'paw.radzikowski@gmail.com';
$domain = trim(strstr(@mail, '@'), '@');

$status = $verifier->verifyDomain($domain); //It should return ListedVerifier::DOMAIN_UNKNOWN
```

#Versions

Version of this composer lib looks like `1.0.201707401` which contains Major version. Minor version. Year, day of the year and commit version. 
It should help with mail repository versioning.
    
