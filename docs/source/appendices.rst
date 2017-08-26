.. _appendices:

Appendices
==========

.. _stix_dev_libraries:

STIX Development Libraries
--------------------------

`Subject: Re: [cti-users] Re: Announcing python-stix2`_

.. _Subject\: Re\: [cti-users] Re\: Announcing python-stix2: http://markmail.org/message/c5ahr2ykpcxxhfar

.. code-block:: none

    Sender: <cti-users@lists.oasis-open.org>
    Delivered-To: mailing list cti-users@lists.oasis-open.org
    Received: from lists.oasis-open.org (oasis-open.org [66.179.20.138])
        by lists.oasis-open.org (Postfix) with ESMTP id B1A965818580;
        Wed, 15 Mar 2017 09:48:17 -0700 (PDT)
    Message-ID: <58C96F55.4030104@apl.washington.edu>
    Subject: Re: [cti-users] Re: Announcing python-stix2
    Date: Wed, 15 Mar 2017 09:44:05 -0700
    From: Stuart Maclean <stuart@apl.washington.edu>
    To: "Back, Greg" <gback@mitre.org>, Eyal Paz <eyalp@checkpoint.com>,
            "cti@lists.oasis-open.org" <cti@lists.oasis-open.org>,
            "cti-users@lists.oasis-open.org" <cti-users@lists.oasis-open.org>
    References: <AAD76FB4-D5FE-41FA-9BDD-1EE6BBE4062D@mitre.org>
            <2956157C13955D458A922DDE028FEE7E0209A8F61D@IL-EX10.ad.checkpoint.com>
            <D3938F78-9B27-48B2-87BA-E57803DEBA81@mitre.org>
    In-Reply-To: <D3938F78-9B27-48B2-87BA-E57803DEBA81@mitre.org>
    
    On 03/15/2017 09:22 AM, Back, Greg wrote:
    >
    > Hi Eyal,
    >
    > MITRE isn't working on anything, and I'm not personally aware of
    > anyone else who is either. But if someone is, hopefully they're on one
    > of these lists and will respond.
    >
    > Greg
    
    Greg, all,
    
    I have followed the STIX development over the past couple of years, and
    even developed a Java library for STIX manipulation, see
    https://github.com/uw-dims/stix-java. That was when STIX 1.1 was current.
    
    I watched with some dismay as the XML schema way of doing things in STIX
    1.1 was dismantled in favor of JSON for STIX 2.  While XML schemas are
    complicated, they are very precise, and a document can be checked
    against a schema to assert its validity.  Further, the richness of tools
    for XML schemas, notably the JAXB/xjc tools for Java, gives developers a
    huge leg-up in implementing an API for STIX manipulation.  I just
    cranked the JAXB handle over the .xsd file set, and hey presto I had a
    set of Java classes with which to start my API. 
    
    Going out on a limb here, I also think that Java developers LIKE more
    discipline that Python developers.  Static typing vs duck typing?  The
    XML schema way of representing information is disciplined, and leads to
    fewer 'You meant X? I thought you meant Y' gotchas at runtime.
    Extrapolating, I think the JSON way of data representation is less
    disciplined than the XML way, hence the natural inclination of Python
    developers to prefer JSON.
    
    Looking at the STIX 2 specs, I admire effort the authors must have put
    in.  But from a library builder's point of view, there being no
    machine-ingestable docs (ie the xsd files in STIX 1.1), I am back to
    square one (if I have missed any machine-readable docs, I apologize).
    
    So, in a nutshell, my own feeling is that there will be no Java-language
    STIX 2 manipulation tools, a sad fact, and I sincerely hope I am wrong
    in this respect.  I do know that I won't add to my STIX 1.1 Java effort.
    
    Stuart

    ----

..
