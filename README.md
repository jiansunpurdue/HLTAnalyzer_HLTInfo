HLTAnalyzer_HLTInfo
===================

In the official package, there will be mismatch if event trigger lists are not
the same in one datafile.

Here I try to fix the mismatch with adding branch by the triger list we provided not the trigger list in the event. Then in each event, I looped over all triggers in our trigger list and find the index, find the trigger decision, prescaler and trigger objects.

fix the mismatch if the evet trigger lists in one file are not the same

The code are developed in CMSSW_5_3_16 with the official HLTrigger/HLTAnalyzer package
