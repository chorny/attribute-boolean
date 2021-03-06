# NAME

Attribute::Boolean - Mark scalars as pure booleans

# VERSION

Version v1.0.6

# SYNOPSYS

This allows you to flag a variable as a boolean.
In numeric context, it will have the value 0 or 1.
In string context is will have the value "false" or "true".
In JSON, it will correctly return false or true values.

    my $bool : Boolean;
    print $bool;    # "false"
    $bool = (1 + 2 == 3);
    print $bool;    # "true"
    print $bool ? "yes" : "no";  # "yes"
    $bool = false;
    print $bool ? "yes" : "no";  # "no"

# EXPORT

This exports constants true and false.

# USAGE

An attribute can be declared boolean as follows:

    my $bool : Boolean;

or

    my $bool : Boolean = true;

If any perl **true** value is assigned, the variable is true; if a
perl **false** value is assigned, the variable is false.

## true

This returns 1 in numeric context, "true" in string context.

## false

This returns 0 in numeric context, "false" in string context.

## TO\_JSON

Provided that convert\_blessed is set on the JSON (or JSON::XS) object,
the variable will correctly convert to JSON true or false.

    my $json = new JSON;
    $json->pretty->convert_blessed;
    my $bool : Boolean;
    my %hash = (
        value => $bool,
        me    => true,
    );
    print $json->encode(\%hash);    # {
                                    #     "value" : false,
                                    #     "me"    : true
                                    # }
                                    

# AUTHOR

Cliff Stanford, `<cpan@may.be>`

# BUGS

Please report any bugs or feature requests to `bug-attribute-boolean+ at rt.cpan.org`, or through
the web interface at [http://rt.cpan.org/NoAuth/ReportBug.html?Queue=attribute-boolean+](http://rt.cpan.org/NoAuth/ReportBug.html?Queue=attribute-boolean+).  I will be notified, and then you'll
automatically be notified of progress on your bug as I make changes.

# SUPPORT

You can find documentation for this module with the perldoc command.

    perldoc Attribute::Boolean

# ACKNOWLEDGEMENTS

Alan Haggai Alavi `<alanhaggai@alanhaggai.org>` for his
[Scalar::Boolean](https://metacpan.org/pod/Scalar::Boolean) module  which was the inspiration
for this module.

# LICENCE AND COPYRIGHT

Copyright 2014 Cliff Stanford.

This program is free software; you can redistribute it and/or modify it
under the same terms as Perl itself.
