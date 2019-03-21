---
date: 2015-12-14 14:14
---
# Differences of Jenkins vs Hudson  for Plugin Developers

As many people may remember, when Oracle bought Sun Microsystems
in 2009/2010 it made a lot of management errors in the communication
with the Open Source communities that had evolved around software
iniated by Sun. One of these projects was the Hudson CI server which
made its lead developer Kohsuke Kawaguchi to leave Oracle in January
2010. He was still contracted by Oracle but according to
[his LinkedIn profile](https://www.linkedin.com/in/kohsukekawaguchi)
he went to work full time for CloudBees since November 2010, a
startup that he was helping to found (coming
[out of stealth-mode](https://www.cloudbees.com/blog/welcome-cloudbees)
in August 2010). There was a famous argument about copyright,
governance and naming rights on Hudson and its source code in
January 2011, which finally led to the creation of a fork named
Jenkins being backed by CloudBees/Kohsuki.

Many developers from the open-source community followed the example
switching from Hudson to Jenkins. To stop the tendency Oracle made
a move to relinquish the governance by moving the Hudson project
to the Apache Foundation in May 2011. The donation was completed
in late 2012  and while seeing a lower number of commits and a
lower number of registered plugins the Hudson project is in a
healthy state and in a steady development. Even years after
theres no sign that one of the forks will die soon.

This brings about the question whether it is possible to write a
plugin that would work for both Hudson and Jenkins. So  how big
are the differences between Jekins and Hudson? Quite amazingly,
the differences are still small. It can be explained by the fact
that the central CI server code needs to be kept as stable as
possible to allow most third-party plugins to continue to work
across changes to the core code.

In March 2014 Anthony Dahanne was looking into
[Developing a plugin for both Jenkins and Hudson](https://blog.dahanne.net/2014/03/09/developing-a-plugin-for-both-jenkins-and-hudson/)
showing his results at the EclipseCon North America 2014
they have since published his slideshow, see
[EclipseCon -  Writing a Hudson / Jenkins plugin](https://www.eclipsecon.org/na2014/session/writing-hudson-jenkins-plugin). 
This is a very good read.

Essentially, the source code just needs to change some import
statements, but the basic layout with the Jenkins Jelly code
is still the same. Due to differences in the governance, the
community registration of the plugin is quite different for
the two projects but in the end there is a build server to
actually compile the source code in the respective environment.
In the end it seems to be easy to port a plugin back and forth
and as such, a company is not bound to either Huddson or Jenkins
when deciding for a plugin development. Just do it.
