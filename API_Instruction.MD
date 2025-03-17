POSTMAN API TESTING INSTRUCTIONS
Endpoints: 
Invoke URL: https://hv3dg0bou5.execute-api.us-east-1.amazonaws.com/v1/user
Path : v1/user method : POST (user register)
Body : 
{
  "operation": "register",
  "username": "testuser",
  "password": "testpassword",
  "email": "test@example.com",
  "phone": "1234567890"
} 

Path : v1/user/{userId}/invoices  method : POST (create invoices)
Body : 
{
  "pathParameters": {
    "user_id": "xxxxx"
  },
  "body": {
    "params": {
      "customization_id": "urn:cen.eu:en16931:2017#conformant#urn:fdc:peppol.eu:2017:poacc:billing:international:aunz:3.0",
      "profile_id": "urn:fdc:peppol.eu:2017:poacc:billing:01:1.0",
      "issue_date": "2025-03-17",
      "due_date": "2025-08-30",
      "invoice_type_code": "380",
      "note": "Tax invoice",
      "document_currency_code": "AUD",
      "accounting_cost": "4025:123:4343",
      "buyer_reference": "0150abc",
      "supplier_endpoint_id": "47555222000",
      "supplier_id": "47555222000",
      "supplier_name": "Supplier Trading Name Ltd",
      "supplier_street_name": "Main street 1",
      "supplier_additional_street_name": "Postbox 123",
      "supplier_city_name": "Harrison",
      "supplier_postal_zone": "2912",
      "supplier_country_code": "AU",
      "supplier_company_id": "47555222000",
      "supplier_registration_name": "Supplier Official Name Ltd",
      "supplier_company_legal_form": "Partnership",
      "supplier_contact_name": "Ronald MacDonald",
      "supplier_contact_telephone": "Mobile 0430123456",
      "supplier_contact_email": "ronald.macdonald@qualitygoods.com.au",
      "customer_endpoint_id": "91888222000",
      "customer_id": "91888222000", #ABN
      "customer_name": "Trotters Trading Co Ltd",
      "customer_street_name": "100 Queen Street",
      "customer_additional_street_name": "Po box 878",
      "customer_city_name": "Sydney",
      "customer_postal_zone": "2000",
      "customer_country_code": "AU",
      "customer_company_id": "91888222000", #ABN
      "customer_registration_name": "Buyer Official Name",
      "customer_contact_name": "Lisa Johnson",
      "customer_contact_telephone": "0261234567",
      "customer_contact_email": "lj@buyer.com.au",
      "payment_note": "Payment within 30 days",
      "multiplier_factor": 100,
      "base_amount": 50,
      "line_extension_amount": 1487.4,
      "tax_percent": 10,
      "quantity": 10,
      "item_description": "It's good.",
      "item_name": "Milk"
    }
  }
}

Path : v1/user/{userId}/invoices/{invoiceId}/validate  method : GET (check its validation)
Body :
{
  "pathParameters": {
    "user_id": "xxxxx",
    "invoice_id": "xxxxxxxxxx"
  }
}

path : v1/user/{userId}/invoices/{invoiceId}  method : GET (get an invoice if it exists)
Body :
{
  "pathParameters": {
    "user_id": "xxxxx",
    "invoice_id": "xxxxxxxxxx"
  }
}

path : v1/user/{userId}/invoices/{invoiceId}  method : PUT (update an invoice)
body : 
{
  "pathParameters": {
    "user_id": "xxxxx",
    "invoice_id": "xxxxxxxxxx"
  },
  "body": {
    "params": {
      "customization_id": "Updated Customization ID 2",
      "profile_id": "Updated Profile ID 2",
      "issue_date": "2025-05-01", #must follow PEPPOL schema
      "due_date": "2026-6-31",
      "invoice_type_code": "Updated Invoice Type Code",
      "note": "Updated Note",
      "document_currency_code": "Updated Document Currency Code",
      "accounting_cost": "Updated Accounting Cost",
      "buyer_reference": "Updated Buyer Reference",
      "customer_endpoint_id": "Updated Customer Endpoint ID",
      "customer_id": "Updated Customer ID",
      "customer_name": "Updated Customer Name",
      "customer_street_name": "Updated Customer Street Name",
      "customer_additional_street_name": "Updated Customer Additional Street Name",
      "customer_city_name": "Updated Customer City Name",
      "customer_postal_zone": "Updated Customer Postal Zone",
      "customer_country_code": "Updated Customer Country Code",
      "customer_company_id": "Updated Customer Company ID",
      "customer_registration_name": "Updated Customer Registration Name",
      "customer_contact_name": "Updated Customer Contact Name",
      "customer_contact_telephone": "Updated Customer Contact Telephone",
      "customer_contact_email": "Updated Customer Contact Email",
      "payment_note": "Updated Payment Note",
      "supplier_endpoint_id": "Updated Supplier Endpoint ID",
      "supplier_id": "Updated Supplier ID",
      "supplier_name": "Updated Supplier Name",
      "supplier_street_name": "Updated Supplier Street Name",
      "supplier_additional_street_name": "Updated Supplier Additional Street Name",
      "supplier_city_name": "Updated Supplier City Name",
      "supplier_postal_zone": "Updated Supplier Postal Zone",
      "supplier_country_code": "Updated Supplier Country Code",
      "supplier_company_id": "Updated Supplier Company ID",
      "supplier_registration_name": "Updated Supplier Registration Name",
      "supplier_company_legal_form": "Updated Supplier Company Legal Form",
      "supplier_contact_name": "Updated Supplier Contact Name",
      "supplier_contact_telephone": "Updated Supplier Contact Telephone",
      "supplier_contact_email": "Updated Supplier Contact Email",
      "item_description": "Updated Item Description",
      "item_name": "Updated Item Name",
      "multiplier_factor": 15,
      "base_amount": 200,
      "tax_percent": 12,
      "line_extension_amount": 200
    }
  }
}

path : v1/user/{userId}/invoices/{invoiceId}  method : DELETE (delete an invoice from DynamoDB)
Body :
{
  "pathParameters": {
    "user_id": "xxxxx",
    "invoice_id": "xxxxxxxxxx"
  }
}
