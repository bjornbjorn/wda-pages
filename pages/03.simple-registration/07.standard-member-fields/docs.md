---
title: Standard Member Fields
taxonomy:
    category: docs
---

>>>> The core profile fields have been **removed in EE4** - please migrate to using [Custom Member Fields]((/simple-registration/custom-member-fields) instead.

Unlike native EE, you can also have the user specify the standard EE profile fields on signup. These include;

* Personal website
* Location
* Birthday
* Biography

You use this by specifying the fields you want to allow using the [allow_fields](/simple-registration/tags#expsimple_registrationform) parameter in the form tag:

>>>>> In order to use "allow_fields" you need to set an encryption key in your **system/user/config/config.php** file. If you don't you'll get an error message saying "In order to use the encryption class requires that you set an encryption key in your config file."

```html
{exp:simple_registration:form allow_fields="url|location|bday|bio"}

<table>
    <tr class="odd">
        <td><label for="username"><em class="required">* </em>
            Username</label>&nbsp;</td><td><input type="text" name="username" value="" id="username" class="field" maxlength="50" autocomplete="off"></td></tr>
    <tr class="even">
        <td><label for="password"><em class="required">* </em>
            Password</label>&nbsp;</td><td><input type="password" name="password" value="" id="password" class="field" maxlength="40" autocomplete="off"></td></tr>
    <tr class="odd">
        <td><label for="password_confirm"><em class="required">* </em>
            Confirm Password</label>&nbsp;</td><td><input type="password" name="password_confirm" value="" id="password_confirm" class="field" maxlength="40" autocomplete="off"></td></tr>
    <tr class="even">
        <td><label for="screen_name">Screen Name</label>&nbsp;</td><td><input type="text" name="screen_name" value="" id="screen_name" class="field" maxlength="50"></td></tr>
    <tr class="odd">
        <td><label for="email"><em class="required">* </em>
            Email Address</label>&nbsp;</td><td><input type="text" name="email" value="" id="email" class="field" maxlength="72" autocomplete="off"></td></tr>
    <tr class="odd">
        <td><label for="bday_y">Birthday</label></td><td><select name="bday_y" id="bday_y">
        <option value="" selected="selected">Year</option>
        <option value="2012">2012</option>
        <option value="2011">2011</option>
        <option value="2010">2010</option>
        <option value="2009">2009</option>
        <option value="2008">2008</option>
        <option value="2007">2007</option>
        <option value="2006">2006</option>
        <option value="2005">2005</option>
        <option value="2004">2004</option>
        <option value="2003">2003</option>
        <option value="2002">2002</option>
        <option value="2001">2001</option>
        <option value="2000">2000</option>
        <option value="1999">1999</option>
        <option value="1998">1998</option>
        <option value="1997">1997</option>
        <option value="1996">1996</option>
        <option value="1995">1995</option>
        <option value="1994">1994</option>
        <option value="1993">1993</option>
        <option value="1992">1992</option>
        <option value="1991">1991</option>
        <option value="1990">1990</option>
        <option value="1989">1989</option>
        <option value="1988">1988</option>
        <option value="1987">1987</option>
        <option value="1986">1986</option>
        <option value="1985">1985</option>
        <option value="1984">1984</option>
        <option value="1983">1983</option>
        <option value="1982">1982</option>
        <option value="1981">1981</option>
        <option value="1980">1980</option>
        <option value="1979">1979</option>
        <option value="1978">1978</option>
        <option value="1977">1977</option>
        <option value="1976">1976</option>
        <option value="1975">1975</option>
        <option value="1974">1974</option>
        <option value="1973">1973</option>
        <option value="1972">1972</option>
        <option value="1971">1971</option>
        <option value="1970">1970</option>
        <option value="1969">1969</option>
        <option value="1968">1968</option>
        <option value="1967">1967</option>
        <option value="1966">1966</option>
        <option value="1965">1965</option>
        <option value="1964">1964</option>
        <option value="1963">1963</option>
        <option value="1962">1962</option>
        <option value="1961">1961</option>
        <option value="1960">1960</option>
        <option value="1959">1959</option>
        <option value="1958">1958</option>
        <option value="1957">1957</option>
        <option value="1956">1956</option>
        <option value="1955">1955</option>
        <option value="1954">1954</option>
        <option value="1953">1953</option>
        <option value="1952">1952</option>
        <option value="1951">1951</option>
        <option value="1950">1950</option>
        <option value="1949">1949</option>
        <option value="1948">1948</option>
        <option value="1947">1947</option>
        <option value="1946">1946</option>
        <option value="1945">1945</option>
        <option value="1944">1944</option>
        <option value="1943">1943</option>
        <option value="1942">1942</option>
        <option value="1941">1941</option>
        <option value="1940">1940</option>
        <option value="1939">1939</option>
        <option value="1938">1938</option>
        <option value="1937">1937</option>
        <option value="1936">1936</option>
        <option value="1935">1935</option>
        <option value="1934">1934</option>
        <option value="1933">1933</option>
        <option value="1932">1932</option>
        <option value="1931">1931</option>
        <option value="1930">1930</option>
        <option value="1929">1929</option>
        <option value="1928">1928</option>
        <option value="1927">1927</option>
        <option value="1926">1926</option>
        <option value="1925">1925</option>
        <option value="1924">1924</option>
        <option value="1923">1923</option>
        <option value="1922">1922</option>
        <option value="1921">1921</option>
        <option value="1920">1920</option>
        <option value="1919">1919</option>
        <option value="1918">1918</option>
        <option value="1917">1917</option>
        <option value="1916">1916</option>
        <option value="1915">1915</option>
        <option value="1914">1914</option>
        <option value="1913">1913</option>
        <option value="1912">1912</option>
        <option value="1911">1911</option>
        <option value="1910">1910</option>
        <option value="1909">1909</option>
        <option value="1908">1908</option>
        <option value="1907">1907</option>
        <option value="1906">1906</option>
        <option value="1905">1905</option>
    </select> <select name="bday_m" id="bday_m">
        <option value="" selected="selected">Month</option>
        <option value="01">January</option>
        <option value="02">February</option>
        <option value="03">March</option>
        <option value="04">April</option>
        <option value="05">May</option>
        <option value="06">June</option>
        <option value="07">July</option>
        <option value="08">August</option>
        <option value="09">September</option>
        <option value="10">October</option>
        <option value="11">November</option>
        <option value="12">December</option>
    </select> <select name="bday_d" id="bday_d">
        <option value="" selected="selected">Day</option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
        <option value="20">20</option>
        <option value="21">21</option>
        <option value="22">22</option>
        <option value="23">23</option>
        <option value="24">24</option>
        <option value="25">25</option>
        <option value="26">26</option>
        <option value="27">27</option>
        <option value="28">28</option>
        <option value="29">29</option>
        <option value="30">30</option>
        <option value="31">31</option>
    </select></td></tr>

    <tr class="even">
        <td><label for="url">URL</label></td><td><input type="text" name="url" value="http://" id="url" class="field" maxlength="150"></td></tr>

    <tr class="odd">
        <td><label for="location">Location</label></td><td><input type="text" name="location" value="" id="location" class="field" maxlength="50"></td></tr>


    <tr class="even">
        <td><label for="occupation">Occupation</label></td><td><input type="text" name="occupation" value="" id="occupation" class="field" maxlength="80"></td></tr>

    <tr class="odd">
        <td><label for="interests">Interests</label></td><td><input type="text" name="interests" value="" id="interests" class="field" maxlength="120"></td></tr>
    <tr class="even">
        <td><label for="aol_im">AOL IM</label></td><td><input type="text" name="aol_im" value="" id="aol_im" class="field" maxlength="50"></td></tr>

    <tr class="odd">
        <td><label for="icq">ICQ</label></td><td><input type="text" name="icq" value="" id="icq" class="field" maxlength="50"></td></tr>


    <tr class="even">
        <td><label for="yahoo_im">Yahoo IM</label></td><td><input type="text" name="yahoo_im" value="" id="yahoo_im" class="field" maxlength="50"></td></tr>


    <tr class="odd">
        <td><label for="msn_im">MSN IM</label></td><td><input type="text" name="msn_im" value="" id="msn_im" class="field" maxlength="50"></td></tr>

    <tr class="even">
        <td><label for="bio">Bio</label></td><td><textarea name="bio" cols="90" rows="12" id="bio"></textarea></td></tr>


</table>

<p><input type="submit" value="Register account"/></p>
{/exp:simple_registration:form}
```
