Torpedo
=======

Description
-----------

Fire when ready. Fast Ruby integration tests for OpenStack.

Installation
------------

1. Install the Gem.
2. Create the torpedo.conf file in your HOME directory.
3. Source novarc for your OpenStack Compute account.

```bash
	gem install torpedo

    cat > ~/.torpedo.conf <<"EOF_CAT"
	# YAML config file for torpedo

	# timeouts
	server_build_timeout: 420
	ping_timeout: 60
	ssh_timeout: 60

	# SERVER test settings
	test_create_image: false
	test_rebuild_server: false
	test_resize_server: false

	# IMAGES (Set one of the following)
	image_name: Ubuntu Natty (11.04)
	#image_ref:

	# FLAVORS (Set one of the following)
	#flavor_name: 
	flavor_ref: 4

	# SSH KEYS (used to verify installations which support personalities)
	#ssh_private_key: <your home dir>/.ssh/id_rsa
	#ssh_public_key: <your home dir>/.ssh/id_rsa.pub

	# KEYPAIRS (used to verify AMI style images)
	#keypair: test.pem
	#keyname: test
	EOF_CAT

	source novarc
```

Examples
--------

Available torpedo tasks:

	Tasks:
	  torpedo all          # Run all tests.
	  torpedo fire         # Fire away! (alias for all)
	  torpedo flavors      # Run flavors tests for the OSAPI.
	  torpedo help [TASK]  # Describe available tasks or one specific task
	  torpedo images       # Run images tests for the OSAPI.
	  torpedo limits       # Run limits tests for the OSAPI.
	  torpedo servers      # Run servers tests for the OSAPI.

Run all tests:

	torpedo fire

Run all tests with debug HTTP request response output:

	DEBUG=true torpedo fire

Run all tests and output an XML report (Ruby 1.8.x only):

	torpedo fire --xml-report=FILE

Payload
--------

* list flavors
* get flavor
* list images
* get image
* list limits
* create server (ping and ssh test)
* delete server metadata items
* update one server metadata item
* update multiple server metadata items
* set server metadata items
* clear server metadata
* create image
* rebuild server (ping and ssh test)
* resize server (ping and ssh test)
* resize confirm (ping and ssh test)
* delete image metadata
* update one image metadata item
* update multiple image metadata items
* set image metadata items
* clear image metadata

License
-------
Copyright (c) 2011 Dan Prince. See LICENSE.txt for further details.
