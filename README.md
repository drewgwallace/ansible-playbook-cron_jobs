This repository is a WORK IN PROGRESS

----

# Ansible Role

## Purpose
  This role is the start to some basic cron jobs that would be useful for most any server running apt-get (Debian based). It is meant to integrate with my [ansible postfix](https://github.com/drewgwallace/ansible-playbook-postfix_nullclient) playbook to generate periodic email updates.

----

## Invokation

<pre>
    - hosts: all
      tasks:
      - include_role:
          name: drewgwallace.ansible-role-cron_jobs
          vars:
            email: "root@localhost"
</pre>

  ### Variables:
  
    email: Email to target for cron job messages

----

## Notes

  ### What is update.rmail.log???
  
  The job listed as "Email rmail.log files" is designed to scrape those log files to be emailed with a standard mail client to update  recipients on various system log entries. It is easy to add log output to these files from various programs/scripts/services that can keep someone informed without going to more feature-rich advanced monitoring solutions.

  ### Why are some of the plays commented out?
  This is related to why the repository is marked a work in progress. There is a [bug in Debian](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=814345) that is causing unattended Ubuntu 16.04 systems to fill their /var/tmp/ directory. Autonomously fully patching and upgrading non-critical systems has some tweaks to be done before it can avoid breaking itself.
