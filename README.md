HLTAnalyzer_HLTInfo
===================

In the official package, there will be mismatch if the event trigger lists are not
the same in one datafile. In the officical version of HLTInfo.cc (HLTInfo.cc_ini in my src), 
we add the branch with the trigger list of the 1st event. Then we assume the trigger list of other events
are the same with the one of the 1st event and fill the trigger decision. However, 
it is not always this case. Then there will be mismatch.

For detailed information of mismatch, you can have a look at "out_hlt_5316_first", which
I got with the official code (with HLTInfo.cc_ini). In the file, you can see, from 129th event, 

Filling decision itrig  :  4      trigName:     HLT_HIL1CaloMonitor_v1

this trigger is added to the trigger list. But we are still filling the trigger decision
according the the branch we set up with the trigger list of 1st event. So we will fill
the wrong thing to the branch.

The soluion is to fill the trigger decision by the trigger name not the index.

Here I try to fix the mismatch with adding branch by the triger list we provided not the trigger 
list in the event. Then in each event, I looped over all triggers in our trigger list and find the 
index, find the trigger decision, prescaler and trigger objects. The trigger list I used is in file
hltanalysis_cff.py  You can just add the triggers you are interested

In src and interface directory, there are two versions of HLTInfo.h and HLTInfo.cc with the fix for
with trigger objects and without trigger objects.

HLTInfo.cc_listbranch_noobj and HLTInfo.cc_listbranch_obj (same for HLTInfo.h) are the two versions
with the fix. Other files are just backups.

The code are developed in CMSSW_5_3_16 with the official HLTrigger/HLTAnalyzer package


And this is the first verion with the fix. Please tell me if you find problems with the new code.

Thanks.
