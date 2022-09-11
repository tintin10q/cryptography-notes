---
title: exaustive_key_search
author: Quinten Cabo s1027427
date: \today
---

# Description 

Exhaustive key search is an attack that you can always try on any security thing involving keys that is not [otp encryption](otp.md). The attack is the most basic attack.

# Steps 

1. Get a C
2. Try a key to decrypt C to get M
3. If M looks sensible you probably tried the right key
4. If M does not look sensible go back to step 2. 

You can't do much to prevent this attack the only thing you can do is to make the number of keys you can try sufficiently large so that there are just too many options.

Generally you will find the key after you have tried about half of all the possible keys. 

This means exausitve key search decreases security strengtht by a factor of 2. 



