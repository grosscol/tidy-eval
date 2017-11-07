---
layout: slide
title: "Validating"
---

{% highlight sh %}
terraform validate
{% endhighlight %}

<section markdown="1">
Validate your root module

{% highlight sh %}
Error validating: 3 error(s) occurred:

* Variable 'security_groups': duplicate found. Variable names must be unique.
* output 'role': unknown resource 'aws_iam_role.bast' referenced in variable aws_iam_role.bast.name
* resource 'aws_instance.bast' config: unknown resource 'aws_iam_instance_profile.bast' referenced in variable aws_iam_instance_profile.bast.name
{% endhighlight %}
</section>

<section markdown="1">

Validate your imported modules
{% highlight sh %}
There are warnings and/or errors related to your configuration. Please
fix these before continuing.

Errors:

  * module.bastion_host.aws_instance.bast: 1 error(s) occurred:

  * module.bastion_host.aws_instance.bast: At column 14, line 1: list "var.subnets" does not have any elements so cannot determine type. in:

  ${var.subnets[0]}
{% endhighlight %}
</section>
