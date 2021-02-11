
## @FILE820.txt
```
//***FILE 820 is from Richard D. Harper and contains his "Private   *   FILE 820
//*           64/20 z/OS Assembly Language Development Platform".   *   FILE 820
//*                                                                 *   FILE 820
//*           email:  mrharper@emailhosting.com                     *   FILE 820
//*                                                                 *   FILE 820
//*     Partial Description of this Package. For a full             *   FILE 820
//*     descripton please see member @@@DOC which is in MSWORD      *   FILE 820
//*     format.  (It must be downloaded in Binary to a PC.)         *   FILE 820
//*                                                                 *   FILE 820
//*     Also included is the same doc as member @@@PDF, which       *   FILE 820
//*     is in PDF format.                                           *   FILE 820
//*                                                                 *   FILE 820
//*     This text comes from the @@@DOC member of this pds.         *   FILE 820
//*                                                                 *   FILE 820
//*     Welcome to my world.                                        *   FILE 820
//*                                                                 *   FILE 820
//*     What I'm about to show you in the pages that follow is      *   FILE 820
//*     my Personal 64/20 z/OS Assembly Language Development        *   FILE 820
//*     Platform.  The 64 in the name refers to having full         *   FILE 820
//*     support for 64-bit z/Architecture.  And the 20              *   FILE 820
//*     represents the 20-Bit displacement instruction set          *   FILE 820
//*     with the 'Y' and 'G' instructions.   Those 20-bit           *   FILE 820
//*     instructions are awesomely powerful in that they allow      *   FILE 820
//*     for direct addressability of one megabyte of storage.       *   FILE 820
//*     So, if we limit our coding to these instructions we         *   FILE 820
//*     can have 256 base registers for the price of one.  To       *   FILE 820
//*     support this reality, this system includes the SSY          *   FILE 820
//*     macros to be used as a replacement for the SS               *   FILE 820
//*     instruction set, which cannot be converted to 20-bit        *   FILE 820
//*     instructions due to the limitations of the hardware.        *   FILE 820
//*     It would require 8-byte instructions and the hardware       *   FILE 820
//*     won't support that, because the PSW cannot represent        *   FILE 820
//*     an 8-byte instruction in the ILC, the Instruction           *   FILE 820
//*     Length Code.                                                *   FILE 820
//*                                                                 *   FILE 820
//*     There are many features to this system, including           *   FILE 820
//*     Stacking DSA for your below-the-line storage, Stacking      *   FILE 820
//*     ATB for your above-the-bar storage, and label level         *   FILE 820
//*     tracing is built into the system, which makes debugging     *   FILE 820
//*     and maintenance a breeze.  These traces support multiple    *   FILE 820
//*     TCBs with a separate SYSOUT dataset being dynamically       *   FILE 820
//*     allocated for each task in the address space.  And full     *   FILE 820
//*     support for programs running in ARMODE is also provided.    *   FILE 820
//*                                                                 *   FILE 820
//*     So, it's a pretty robust system.  And it's the only         *   FILE 820
//*     true 64/20 Development Platform in the world.  I know,      *   FILE 820
//*     because I had to write GETMAIN and FREEMAIN for             *   FILE 820
//*     above-the-bar storage, and you can't have a truly           *   FILE 820
//*     effective 64/20 system without that.  In ten years IBM      *   FILE 820
//*     has failed to produce that result, so I had to do it        *   FILE 820
//*     myself.  It's part of this system.   I hope you will        *   FILE 820
//*     find it as useful as I do.                                  *   FILE 820
//*                                                                 *   FILE 820
//*  What You Can and Cannot Do With This System                    *   FILE 820
//*                                                                 *   FILE 820
//*      You have to understand that this system, as                *   FILE 820
//*      distributed is subject to the GNU-GPL license, which       *   FILE 820
//*      means that it cannot be used to write or develop           *   FILE 820
//*      commercial code, which is to say code intended for         *   FILE 820
//*      sale or production use by any company.  You can't do       *   FILE 820
//*      that, the GNU-GPL precludes that, which is why I           *   FILE 820
//*      distributed it this way.                                   *   FILE 820
//*                                                                 *   FILE 820
//*  What you can do.                                               *   FILE 820
//*                                                                 *   FILE 820
//*      Now that said, there are still a lot of reasons to use     *   FILE 820
//*      this platform.  Any code that is not for sale or for       *   FILE 820
//*      production use is not a problem.  You can do whatever      *   FILE 820
//*      you want as long as you're not intending to sell what      *   FILE 820
//*      you write with this platform.  So, let's talk about        *   FILE 820
//*      what you can do.                                           *   FILE 820
//*                                                                 *   FILE 820
//*      You can write any kind of test program that you like,      *   FILE 820
//*      and we all need to write test programs to test out         *   FILE 820
//*      our production code.  Well, I'm distributing some 30+      *   FILE 820
//*      such programs with this system in the /TST library.        *   FILE 820
//*                                                                 *   FILE 820
//*      When I was working with JES2, that group had two           *   FILE 820
//*      people where there whole job was to write test             *   FILE 820
//*      programs to test out new interfaces placed into the        *   FILE 820
//*      component, such as SAPI, Extended Status, and the          *   FILE 820
//*      like.  Such testers can certainly use this system to       *   FILE 820
//*      develop these kinds of programs, since they were           *   FILE 820
//*      never intended for sale in the first place.  And this      *   FILE 820
//*      is true for any company and any developer anywhere.        *   FILE 820
//*      Yes, it's Free Software, but who gives a damn, it's a      *   FILE 820
//*      bloody test program.                                       *   FILE 820
//*                                                                 *   FILE 820
//*      And this is a sanctioned use for the GNU-GPL version       *   FILE 820
//*      of this system.  You, as the developer will likely         *   FILE 820
//*      find yourself many times more productive than the          *   FILE 820
//*      developer sitting in the cubicle next to you, if you       *   FILE 820
//*      learn this system and use it.  And in today's job          *   FILE 820
//*      market that can only work to your advantage, as it         *   FILE 820
//*      will benefit you and your company.                         *   FILE 820
//*                                                                 *   FILE 820
//*      The other really important use for this system is for      *   FILE 820
//*      your own education or edification.  We all have to         *   FILE 820
//*      remain current in our knowledge and understanding of       *   FILE 820
//*      the z/OS Operating System.  It's our job and               *   FILE 820
//*      continuing education is a part of that job.  Every         *   FILE 820
//*      few years IBM comes out with a new version of POPs         *   FILE 820
//*      (Principles of Operations), and every time a new           *   FILE 820
//*      version comes out you need to read it, and I mean          *   FILE 820
//*      cover to cover.  They're constantly adding new             *   FILE 820
//*      instructions.  I'm still not really clear about the        *   FILE 820
//*      damn PLO instruction.                                      *   FILE 820
//*                                                                 *   FILE 820
//*      But this is a system that allows you to test out new       *   FILE 820
//*      instructions where you can use the #TRACE macro to         *   FILE 820
//*      get a clear and distinct understanding of how these        *   FILE 820
//*      new instructions work.  But it's not just new              *   FILE 820
//*      instructions.  If you haven't done an MGCR, write a        *   FILE 820
//*      test program that uses it.  If you haven't written an      *   FILE 820
//*      SRB, do so.  If you haven't written a PC, write one,       *   FILE 820
//*      and use this system to do it.  You will learn more         *   FILE 820
//*      quickly for it.  Ongoing education is important, and       *   FILE 820
//*      something you need to do committedly if you're             *   FILE 820
//*      working in this field.  So, this is another                *   FILE 820
//*      legitimate and sanctioned use of this system.              *   FILE 820
//*                                                                 *   FILE 820
//*      Another thing you can do is use it to debug your           *   FILE 820
//*      production code.  Then you can cut and paste the           *   FILE 820
//*      debugged code into your production code, as long as        *   FILE 820
//*      you don't include any of my macros in that production      *   FILE 820
//*      code.  This platform can help you to diagnose              *   FILE 820
//*      problems much more quickly, and help you to be much        *   FILE 820
//*      more productive than the other developers in your          *   FILE 820
//*      shop.  And this is also a sanctioned use of the            *   FILE 820
//*      GNU-GPL version of this code.                              *   FILE 820
//*                                                                 *   FILE 820
//*  What you can't do.                                             *   FILE 820
//*                                                                 *   FILE 820
//*      This is a macro based system, and as such anything         *   FILE 820
//*      you write using this platform will inherently include      *   FILE 820
//*      code that I have written which is subject to GNU-GPL       *   FILE 820
//*      and this makes anything that you write using this          *   FILE 820
//*      platform also subject to GNU-GPL.  And what that           *   FILE 820
//*      means is that anything you write using this platform       *   FILE 820
//*      cannot be sold, it must be given away for free, as         *   FILE 820
//*      Free Software.  Understand?                                *   FILE 820
//*                                                                 *   FILE 820
//*      But even more than that, as I understand the GNU-GPL       *   FILE 820
//*      license, nothing that you write using this platform        *   FILE 820
//*      can be linked-in or included into any commercial           *   FILE 820
//*      application, because if it is, the entire application      *   FILE 820
//*      cannot be sold and must be given away for free, as         *   FILE 820
//*      Free Software.                                             *   FILE 820
//*                                                                 *   FILE 820
//*      So, this is something you need to be very careful of,      *   FILE 820
//*      as a developer.  You cannot use the Free Software          *   FILE 820
//*      version of this code to write a subroutine or              *   FILE 820
//*      sub-program and include the object module into ANY         *   FILE 820
//*      commercial code.  So, if you do your boss will very        *   FILE 820
//*      likely be really mad.  So don't do that.                   *   FILE 820
//*                                                                 *   FILE 820
//*      So, in that event your two options are, remove the         *   FILE 820
//*      code from the commercial product and move on, or if        *   FILE 820
//*      it was really good code that you want to keep, you         *   FILE 820
//*      can purchase a commercial license for this                 *   FILE 820
//*      development platform from me or my representative.         *   FILE 820
//*                                                                 *   FILE 820
//*      Another thing that you can't do, well it's not that        *   FILE 820
//*      you can't do, but it would be very unwise to do, is        *   FILE 820
//*      to write any production code with this system.  You        *   FILE 820
//*      see, anything written with the GNU-GPL version of          *   FILE 820
//*      this code is by definition "Free Software."  So, if        *   FILE 820
//*      you're working for a bank and write something cool         *   FILE 820
//*      like an Investment Portfolio System, which I did once      *   FILE 820
//*      long ago, and use this system to do it?  Well, it's        *   FILE 820
//*      free software.  So any employee can take that code and     *   FILE 820
//*      give it away to any competitor for free.  So, you          *   FILE 820
//*      really don't want use this system for production code.     *   FILE 820
//*      In that event the company needs to purchase a              *   FILE 820
//*      Commercial License from me or my representative.           *   FILE 820
//*                                                                 *   FILE 820
```

