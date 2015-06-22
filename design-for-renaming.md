Design for Renaming
===================

Emma Humphries (http://emmah.net) 

^ I work on the web to app funnel at Peel Technologies

^ Previously I've worked on web apps at Apple, enterprise web security tools at WhiteHat, and on several projects, including Identity at Linden Lab

^ I recently changed my name, and consequently have run into a variety of experiences, good and bad online as a result

^ I also wrote the original [Unitarian Universalist Jihad Name Generator](http://emmah.net/ujname.html), so if that doesn't establish my bona fides.

Caveats
-------

^ I'm an engineer

^ I'm not a IA: I can't tell you how to redesign your views in the system

^ IANAL: This does not constitute legal advice

^ And this is, for now, a US-Centric talk

What I'm Going to Cover
-----------------------

* Why does this matter
* Rules of Thumb
    * Ask yourself what names your system need?
    * Computers are good at microaggressions
    * Everyone has many names
    * The State is Transphobic by Nature (but you don't have to be.)
* Things To Do
* Questions

Why Does This Matter
--------------------

* The size of the issue
    * We know that for better or worse, around 80% of women-identified US residents change their name on marriage
    * Despite that most States include a legal name change when you marry, you're still going to have to change bank accounts, credit cards, medical records, and several online accounts

Prior Art
---------

* [Falsehoods Programmers Believe About Names](http://www.kalzumeus.com/2010/06/17/falsehoods-programmers-believe-about-names/)
* [Personal Names Around the World](http://www.w3.org/International/questions/qa-personal-names) (W3C)

Things To Do
------------

* Audit names in your systems
    * Where are names exposed to users
    * Where are names exposed to CSRs
    * Do you need to store a wallet name?
* If you must keep a user/customer's wallet name, offer a display/preferred name
    * Use it to address the customer everywhere (web, email, phone, postal, apps)
    * Make sure that CSRs see the preferred name first
    * Limit access to wallet names (security, audit)
* Make it easy and clear for people to change names
    * Help system entry
    * Clear process
    * Tell people up front if they have to talk to someone on the phone, provide alternatives
    * Securely handle people documentation (court orders and copies of identity documents are attractive to attackers, state and non-state)

Notes
-----

* The size of the issue
    * Number of people changing the name on their social security accounts each year
    * 7% of Americans Citizens do not have access to Birth Certificate, Naturalization Papers, or Passports (Brennan Center, 2006)
    * 48% of voting age Women with ready access to Birth Certificate have a Birth Certificate with current legal name (Brennan Center, 2006)
    *  11% of American citizens do not have government-issued photo identification (Brennan Center, 2006)
    * 48% of trans people in the US do not have identification matching their correct name (Cite)
    * 46% of American citizens have a US passport (Estmate, the Expeditioner)
    * 80% of American women change their name on marriage.
* Names manage access to things
    * Deeds and Titles
    * Digital things now: music, books, software licences, mobile apps and these things are initmate 

> @danimgrace: Take your husband’s last name. Take his first name. Take his social. Assume his identity. Hide the body in a closet. You’re the husband now. http://twitter.com/danimgrace/status/598204691374280704

LSL Example of Names
--------------------

```
string get_name_for_uuid(key uuid)
{
    // try for a display name
    string name = llGetDisplayName(uuid);
    
    // if name service is down, look up legacy name
    if (name == "???" || name == "")
    {
        name = llKey2Name(uuid);

        // convert name (first, last) to a list
        list parts = llParseString2List(name, [" "], []);
        
        // legacy name of post-display name residents is always "Resident" so throw away that part and return
        // first name as user name
        if (llList2String(parts, 1) == "Resident")
        {
            name = llList2String(parts, 0);                    
        }    
    }
    
    return name;
}
```

Guidelines
----------

* Computers are good at Microaggressions
    * If you make a mistake with a person's name, offer a way to fix it fast.
    * square
* Can you not even with "Real Names"?
    * quote from LL VP about reputations
    * assuming ill intent
* The state is transphobic by nature.
* Even if the state is transphobic, you don't need to be.
* Offer workarounds: Display Names and Preferred Names
    * Kaiser/EPIC
        * Kaiser patient management software allows for preferred names
    * Second Life
        * Display names added in 2010 as a work around for difficulty of changing name 
  * But display names preferred names are inconsistent
    * Software that displays preferred name only accessed by clinical staff, clerks 
      and front office staff see only 3270 terminal with legal name
    * Scripts in SL have to account for SL 
* If I change my name once, change it everywhere
   * amazon
   * paypal

References
----------

* http://www.wired.com/2015/06/facebook-real-name-policy-problems/
* https://www4.uwm.edu/eti/2007/VoterID.htm
* http://www.brennancenter.org/sites/default/files/legacy/d/download_file_39242.pdf
* http://www.theexpeditioner.com/2010/02/17/how-many-americans-have-a-passport-2/
* http://www.kalzumeus.com/2010/06/17/falsehoods-programmers-believe-about-names/
* http://www.w3.org/International/questions/qa-personal-names
