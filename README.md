
## laravel validation 


## Type if validation 

- Accepted
- Active URL
- After (Date)
- Alpha
- Alpha Dash
- Alpha Numeric
- Array
- Before (Date)
- Between
- Boolean
- Confirmed
- Date
- Date Format
- Different
- Digits
- Digits Between
- E-Mail
- Exists (Database)
- Image (File)
- In
- Integer
- IP Address
- Max
- MIME Types
- Min
- Not In
- Numeric
- Regular Expression
- Required
- Required If
- Required With
- Required With All
- Required Without
- Required Without All
- Same
- Size
- String
- Timezone
- Unique (Database)
- URL

and More in laravel 9 


## Documentation validation in Laravel 🔗

[ Documentation laravel 5.0 ](https://laravel.com/docs/5.0/validation)

[Documentation laravel 8.x ](https://laravel.com/docs/8.x/validation)




# Example


### Controller Page 
```bash

    $rules = [
        'name' => 'required',
        'email' => 'required|email',
        'message' => 'required|max:250',
    ];

    $customMessages = [
        'required' => 'The :attribute field is required.'
    ];

    $this->validate($request, $rules, $customMessages);

```
### Page.blade.php  | your page for echo the errors

```bash

    @if ($errors->any())
        <div class="alert alert-danger">
            <ul>
                @foreach ($errors->all() as $error)
                    <li>{{ $error }}</li>
                @endforeach
            </ul>
        </div>
    @endif

```

## Another way 

```bash

    $messsages = [
                'email.required'=>'You cant leave Email field empty',
                'name.required'=>'You cant leave name field empty',
                'name.min'=>'The field has to be :min chars long',
                ];

        $rules = [
                'email'=>'required|unique:content',
                'name'=>'required|min:3',
                ];

    $validator = Validator::make($request, $rules,$messsages);

```
## Or

```bash

    $messsages = array(
		'email.required'=>'You cant leave Email field empty',
		'name.required'=>'You cant leave name field empty',
                'name.min'=>'The field has to be :min chars long',
	);

	$rules = array(
		'email'=>'required|unique:content',
		'name'=>'required|min:3',
	);

	$validator = Validator::make(Input::all(), $rules,$messsages);

```

## More validation

```bash

    $validate = $request->validate([
                'img'       => 'required|image|mimes:jpeg,png,jpg,gif|max:2048',
                'title'     => 'required|string|max:100|min:3',
                'content'   => 'required|string|max:255|min:3',
                'price'     => 'required|string|max:20|min:1',
                'type'      => 'required|string|max:30|min:1',
            ],

            $customMessages = [
                'img.required' => 'الرجاء تحديد صورة للمنتج',
                'img.mimes' => 'مسموح استخدام فقط للصور (jpeg,png,jpg,gif)',
                'required' => 'يحب كتابة الحقول كامله ',
                'title.max' => 'المسموح للعنوان من 3 حروف الى 100 حرف',
                'content.max' => 'المسموح للوصف من 3 حروف الى 255 حرف',
                'price.max' => 'المسموح للسعر من 1 حروف الى 30 حرف',
                'min' => 'المسموح من 3 حروف الى 100 حرف',
            ]
        );

        $this->validate($request, $validate, $customMessages);
    

```
