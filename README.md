Laravel Dotmailer
=================

A very basic Laravel wrapper for the [Dotmailer API Client](https://github.com/romanpitak/dotMailer-API-v2-PHP-client) by [romanpitak](https://github.com/romanpitak).

## Installation

To install, inside your project directory run the following from your terminal:

	composer require industrious-mouse/laravel-dotmailer

Then load the service provider in your config/app.php:

	IndustriousMouse\LaravelDotmailer\LaravelDotmailerServiceProvider::class

You'll also need to publish the config, so you can provide your keys:

	php artisan vendor:publish --provider="IndustriousMouse\LaravelDotmailer\LaravelDotmailerServiceProvider"

## Examples

### Adding a Contact with custom data fields.

	$contact_data = new ApiContact([
		'email'			=> 'test@test.com',
		'emailType'		=> 'Html',
		'dataFields'	=> [
			[
				'key' => 'FIRSTNAME',
				'value' => 'Name'
			]
		]
	]);

	try
	{
	    $contact = Dotmailer::PostContacts($contact_data);
	}
	catch (Exception $e)
	{
	    return $e;
	}

### Sending a Campaign to a contact


	$contact_id = 12345;
	$campaign_id = 12345;

	$data = [
		'CampaignId'		=> $campaign_id,
		'ContactIds'		=> [
			$contact_id
		]
	];

	$send = Dotmailer::PostCampaignsSend(new ApiCampaignSend($data));

	try
	{
		$contact = Dotmailer::PostContacts($contact_data);
	}
	catch (Exception $e)
	{
		return $e;
	}

