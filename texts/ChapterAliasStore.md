# <a name="ChapterAliasStore"></a>Secure Alias Store



## <a name="Payment_v1_Alias_Insert"></a>Alias Insert

This function may be used to insert an alias without knowledge about the card details. Therefore a redirect of the customer is required.

--->>>

```
POST /Payment/v1/Alias/Insert
```

<<<---

#### Request




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RequestHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_RequestHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">General information about the request.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RegisterAlias</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_RegisterAlias">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Registration parameters</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Type</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Type of payment means to register</div>
	<i class="small text-muted">
Possible values: CARD, BANK_ACCOUNT, POSTFINANCE.<br />
					<span>Example: CARD</span>
	</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>ReturnUrls</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_ReturnUrls">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Urls which are to be used to redirect the payer back to the shop.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Styling</strong><br />
	<span class="text-muted small">
		
			<a class="type-details in" href="#Payment_Models_Data_Styling">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Custom styling resource for the Hosted Register form.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>LanguageCode</strong><br />
	<span class="text-muted small">
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Language used for displaying forms.

Code-List:
 de - German
 en - English
 fr - French
 da - Danish
 cs - Czech
 es - Spanish
 hr - Croatian
 it - Italian
 hu - Hungarian
 nl - Dutch
 no - Norwegian
 pl - Polish
 pt - Portuguese
 ru - Russian
 ro - Romanian
 sk - Slovak
sl - Slovenian
 fi - Finnish
sv - Swedish
 tr - Turkish
 el - Greek
 ja - Japanese
 zh - Chinese</div>
	<i class="small text-muted">
					<span>Example: de</span>
	</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Check</strong><br />
	<span class="text-muted small">
		
			<a class="type-details in" href="#Payment_Models_Data_AliasInsertCheck">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Parameters for checking the means of payment before registering.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "RequestHeader": {
    "SpecVersion": "1.3",
    "CustomerId": "[your customer id]",
    "RequestId": "[your request id]",
    "RetryIndicator": 0
  },
  "RegisterAlias": {
    "IdGenerator": "RANDOM"
  },
  "Type": "CARD",
  "ReturnUrls": {
    "Success": "[your shop alias registration success url]",
    "Fail": "[your shop alias registration fail url]"
  }
}
</pre>

<<<---

#### Response




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>ResponseHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_ResponseHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Contains general informations about the response.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Token</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Id for referencing later</div>
	<i class="small text-muted">
					<span>Example: 234uhfh78234hlasdfh8234e</span>
	</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Expiration</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		date
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Expiration date / time of the generated token in ISO 8601 format in UTC. After this time, the token won’t be accepted for any further action.</div>
	<i class="small text-muted">
					<span>Example: 2015-01-30T13:45:22.258+02:00</span>
	</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RedirectUrl</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Saferpay-Url to post the form data to.</div>
	<i class="small text-muted">
					<span>Example: https://www.saferpay.com/VT2/api/...</span>
	</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "ResponseHeader": {
    "SpecVersion": "1.3",
    "RequestId": "[your request id]"
  },
  "Token": "234uhfh78234hlasdfh8234e",
  "Expiration": "2015-01-30T12:45:22.258+01:00",
  "RedirectUrl": "https://www.saferpay.com/vt2/api/..."
}
</pre>

<<<---





## <a name="Payment_v1_Alias_AssertInsert"></a>Alias AssertInsert



--->>>

```
POST /Payment/v1/Alias/AssertInsert
```

<<<---

#### Request




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RequestHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_RequestHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">General information about the request.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Token</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Token returned by initial call.</div>
	<i class="small text-muted">
Id[1..50]<br />
					<span>Example: 234uhfh78234hlasdfh8234e</span>
	</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "RequestHeader": {
    "SpecVersion": "1.3",
    "CustomerId": "[your customer id]",
    "RequestId": "[unique request identifier]",
    "RetryIndicator": 0
  },
  "Token": "234uhfh78234hlasdfh8234e"
}
</pre>

<<<---

#### Response




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>ResponseHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_ResponseHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Contains general informations about the response.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Alias</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_AliasInfo">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Information about the registered alias.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>PaymentMeans</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_PaymentMeansInfo">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Information about the registered means of payment</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "ResponseHeader": {
    "SpecVersion": "1.3",
    "RequestId": "[your request id]"
  },
  "Alias": {
    "Id": "alias35nfd9mkzfw0x57iwx",
    "Lifetime": 1000
  },
  "PaymentMeans": {
    "Brand": {
      "PaymentMethod": "SAFERPAYTEST",
      "Name": "Saferpay Test Card"
    },
    "DisplayText": "9123 45xx xxxx 1234",
    "Card": {
      "MaskedNumber": "912345xxxxxx1234",
      "ExpYear": 2015,
      "ExpMonth": 9,
      "HolderName": "Max Mustermann",
      "CountryCode": "CH"
    }
  }
}
</pre>

<<<---





## <a name="Payment_v1_Alias_InsertDirect"></a>Alias InsertDirect



--->>>

```
POST /Payment/v1/Alias/InsertDirect
```

<<<---

#### Request




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RequestHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_RequestHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">General information about the request.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RegisterAlias</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_RegisterAlias">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Registration parameters</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>PaymentMeans</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_PaymentMeans">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Means of payment to register</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "RequestHeader": {
    "SpecVersion": "1.3",
    "CustomerId": "[your customer id]",
    "RequestId": "[your request id]",
    "RetryIndicator": 0
  },
  "PaymentMeans": {
    "Card": {
      "Number": "912345678901234",
      "ExpYear": 2015,
      "ExpMonth": 9,
      "HolderName": "Max Mustermann",
      "VerificationCode": "123"
    }
  },
  "RegisterAlias": {
    "IdGenerator": "RANDOM"
  }
}
</pre>

<<<---

#### Response




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>ResponseHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_ResponseHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Contains general informations about the response.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>Alias</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_AliasInfo">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Information about the registered alias.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>PaymentMeans</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Payment_Models_Data_PaymentMeansInfo">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Information about the registered means of payment</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "ResponseHeader": {
    "SpecVersion": "1.3",
    "RequestId": "[your request id]"
  },
  "Alias": {
    "Id": "alias35nfd9mkzfw0x57iwx",
    "Lifetime": 1000
  },
  "PaymentMeans": {
    "Brand": {
      "PaymentMethod": "SAFERPAYTEST",
      "Name": "Saferpay Test Card"
    },
    "DisplayText": "9123 45xx xxxx 1234",
    "Card": {
      "MaskedNumber": "912345xxxxxx1234",
      "ExpYear": 2015,
      "ExpMonth": 9,
      "HolderName": "Max Mustermann",
      "CountryCode": "CH"
    }
  }
}
</pre>

<<<---





## <a name="Payment_v1_Alias_Delete"></a>Alias Delete



--->>>

```
POST /Payment/v1/Alias/Delete
```

<<<---

#### Request




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>RequestHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_RequestHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">General information about the request.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>AliasId</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		string
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">The Alias you want to delete</div>
	<i class="small text-muted">
Id[1..40]<br />
					<span>Example: alias35nfd9mkzfw0x57iwx</span>
	</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "RequestHeader": {
    "SpecVersion": "1.3",
    "CustomerId": "[your customer id]",
    "RequestId": "[unique request id]",
    "RetryIndicator": 0
  },
  "AliasId": "alias35nfd9mkzfw0x57iwx"
}
</pre>

<<<---

#### Response




<table class="table">
	<thead>
		<tr>
			<th colspan="2">Arguments</th>
		</tr>
	</thead>
				<tr>
					<td class="col-sm-4 text-right">
	<strong>ResponseHeader</strong><br />
	<span class="text-muted small">
			<span>
				<span class="text-mandatory">mandatory</span>,
			</span>
		
			<a class="type-details in" href="#Common_ResponseHeader">container</a>
	</span>
</td>
<td class="col-sm-8">
	
	<div style="padding-bottom: 10px">Contains general informations about the response.</div>
	<i class="small text-muted">
			</i>
</td>
				</tr>

</table>


--->>>

<p>Example:</p>
<pre class="prettyprint">
{
  "ResponseHeader": {
    "SpecVersion": "1.3",
    "RequestId": "[your request id]"
  }
}
</pre>

<<<---






