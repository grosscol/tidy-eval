---
layout: slide
title: "Statefile"
---
<section markdown="1">
## Before Apply
Size
{% highlight sh %}
wc -l terraform.tfstate
36 terraform.tfstate
{% endhighlight %}

Content tracks no resources nor module outputs
{% highlight json %}
  {
      "version": 3,
      "terraform_version": "0.10.7",
      "serial": 19,
      "lineage": "be45f145-5851-4383-bd36-1f95a802d8c6",
      "modules": [
          {
              "path": [
                  "root"
              ],
              "outputs": {},
              "resources": {},
              "depends_on": []
          }
  }
{% endhighlight %}
</section>

<section markdown="1">
## After Apply
Size
{% highlight sh %}
wc -l terraform.tfstate
592 terraform.tfstate
{% endhighlight %}

Contents has output values and resources
{% highlight json %}
{
    "version": 3,
    "terraform_version": "0.10.7",
    "serial": 20,
    "lineage": "be45f145-5851-4383-bd36-1f95a802d8c6",
    "modules": [
        {
            "path": [
                "root"
            ],
            "outputs": {
                "ELB address": {
                    "sensitive": false,
                    "type": "string",
                    "value": "terraform-example-elb-421228339.us-east-2.elb.amazonaws.com"
                },
                "bastion IP": {
                    "sensitive": false,
                    "type": "string",
                    "value": "18.216.159.1"
                }
            },
            "resources": {
                "aws_elb.web": {
                    "type": "aws_elb",
                    "depends_on": [
                        "aws_instance.web",
                        "aws_security_group.elb",
                        "aws_subnet.default"
                    ],
                    "primary": {
                        "id": "terraform-example-elb",
                        "attributes": {
                            "access_logs.#": "0",
                            "availability_zones.#": "1",
                            "availability_zones.1726430690": "us-east-2b",
                            "connection_draining": "false",
                            "connection_draining_timeout": "300",
                            "cross_zone_load_balancing": "true",
                            "dns_name": "terraform-example-elb-421228339.us-east-2.elb.amazonaws.com",
                            "health_check.#": "1",
                            "health_check.0.healthy_threshold": "10",
                            "health_check.0.interval": "30",
                            "health_check.0.target": "TCP:80",
                            "health_check.0.timeout": "5",
                            "health_check.0.unhealthy_threshold": "2",
                            "id": "terraform-example-elb",
                            "idle_timeout": "60",
                            "instances.#": "1",
                            "instances.790445125": "i-0ca43e65c0d0112db",

{% endhighlight %}
</section>
