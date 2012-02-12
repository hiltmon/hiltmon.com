---
layout: post
title: "Hiltmonism - Fix instead of Blame"
date: 2012-02-11 09:49
comments: true
categories: Hiltmonism
---

*I was saving this one up for later, but events of this week prompted me to write it now.*

Whenever something goes wrong, the first reaction of many people is to find someone else to blame. Arguments and vitriol erupt, things are said or smashed, as each team member tries to protect themselves from being blamed. 

I, for one, do not ever again want to be on a team that does this. Nor should you.

Things go wrong, people make mistakes, software fails. It's what unintentionally happens when us imperfect humans try to create perfection. It's natural and normal. It should be expected, planned for and dealt with.

When something goes wrong, the first reaction of a team *should* be to identify and fix the problem. Find the error, correct it, write a test. Find the design flaw, solve for the best way to fix it, and implement the fix. And then, get back to creating the product you were working on. No blame, no vitriol, just professional calm.

Back in the late 1990's, when I was a Project Manager, several of my engagements were to see if I, as an external person, could jump in and "fix" some broken projects. Its crazy to think back that a 20-something year-old whippersnapper Project Manager would be called in for this, but it shows how messed up these projects were. In all but two cases(<sup id="fnref1"><a href="#fn1" rel="footnote">1</a></sup>), the projects had stalled because things had gone wrong and the team had become lost in a never-ending cycle of blame and coverage, so much so, that they spent all their time doing this and none of of in actually doing the work. The people were angry, hurt and scared they would lose their jobs. Clients were unhappy because they were not getting their projects completed. 

The solution was to get rid of the blaming and get back to the doing. Sounds simple, but hard to implement of you are in the blame circle. As an independent, I could stay out of the fray, focus on the project instead of the anger, and re-motivate the people back to work. To do this, the first thing that had to happen was the removal of any histrionics, what someone said or did before I arrived was taken off the table. Anyone who went back to sayings and doings before I arrived was shot down, and in some cases, taken off the team as they destroyed morale. The second step was to encourage communication again between the team members, it makes it easier when they felt like they were starting from scratch. And the third step was to encourage the now communicating team to find issues, describe the found issues clearly in terms of the product and practice getting together to resolve them. Oh, and blame was banned.

The "what" is wrong is important, not the "who".

Blame incorrectly assumes intent. If someone is blamed for a problem, it is assumed that they intended to create that problem. Why else would they be blamed? *This kind of uninformed, ignorant and just plain stupid assumptive question is what causes blame cycles in the first place.*

Blame also requires defense. If you do not defend yourself, you will get lumped with whatever you are being blamed for, whether right or wrong, and your career will suffer. If you do defend yourself, you're not doing your job, and the project suffers.

Fixing, on the other hand, correctly assumes that the team is focussed on the project, and that they are smart enough to assume things will go wrong. A fixer team works together to get things done. Fixing requires communication to identify the problem, the team to focus only on the problem, and to figure out a solution. Successful teams are always fixers. Their members are free to work without fear or distractions.

I do believe that the issue with blame often boils down to the issue of intent.  Did the person who messed up do so intentionally or unintentionally. It is in this space that the blame thing gets out of hand. Since intent is incorrectly assumed in blaming, the blame then gets spread out far and wide.

This week, it was announced that [Path](https://path.com/) uploaded its user's complete address books to their servers so their "find friends" function could work. The blame cycle went nuts. Path was accused of stealing people's data without their knowledge, people closed their accounts in disgust and the press went wild. The Path CEO tried to calm the waters by explaining why they did this. He honestly though he was doing his user's a favor, and he honestly admitted that Path did nothing untoward with the data. But the blame machine drove this issue quite out of context.

How far, far enough that by the end of the week, Path has apologized, deleted all the data and released a new version of their app that requests permission to do this. Far enough that by the end of the week, the blame machine had found a new target, Apple, for allowing Path to access the address book and allow Path to do this.

The fix, however, for this whole brouhaha is simple, and is used by a lot of developers who do the same thing as Path but are not blamed for doing anything wrong. The fix is to hash the address book data using a one-way hash and to then use these encoded hashes to find friends. With hashes, Path can still match friends, but have no knowledge of who they really are, protecting user privacy. If they get hacked, the data is useless, and they cannot ever share it, because the hashing algorithms are 1-way.

The whole Path issue could have been resolved by just hashing the user's address book. But the blame cycle has probably destroyed their business, and has tarnished the reputation of Apple as well. It was a waste of everything, and wholly undeserved.

So back to fix, not blame Hiltmonism:

*Fixing is productive, blame is a productivity killer. Fixing is fun, blaming is painful. Fixing gets the job done, blaming prevents it. Fixing is good for your career and karma, blaming is not. So why do we tolerate it? Next time the blame cycle starts, nip it in the bud with a "It does not matter who is to blame, we all need to get it fixed" statement and move on.*

*Or leave that team and find a better one.*

---

<div class="footnotes">
    <ol>
        <li id="fn1">The other two were caused by miscommunications between client and team, so the team actually built the wrong software. This all happened before agile development became common, and is why it is so popular and successful now. <a href="#fnref1" rev="footnote">↩</a></li>
    </ol>
</div>
