Using Tablesorter.js to control a series of dynamic tables, I had an issue
where the column required an defined sort, but the columns numbers were
dynamic, so here's a proof of concept.

I do have to redo this to reduce the redundancy.
Maybe tomorrow.

~~~~~


jQuery(document).ready(function()
    {
      var stickColumn  = jQuery("#player_roster_stick table > tbody > tr:first > td").length;
      var gloveColumn  = jQuery("#player_roster_glove table > tbody > tr:first > td").length;
      var pantsColumn  = jQuery("#player_roster_pants table > tbody > tr:first > td").length;
      var skateColumn  = jQuery("#player_roster_skates table > tbody > tr:first > td").length;
      var helmetColumn = jQuery("#player_roster_helmet table > tbody > tr:first > td").length;

      var stickSorter = [];
      var gloveSorter = [];
      var pantsSorter = [];
      var skateSorter = [];
      var helmetSorter = [];

      for (index = 0; index < stickColumn; ++index) {
         stickSorter.push([index,0]);
      }
      for (index = 0; index < gloveColumn; ++index) {
         gloveSorter.push([index,0]);
      }
      for (index = 0; index < pantsColumn; ++index) {
         pantsSorter.push([index,0]);
      }
      for (index = 0; index < skateColumn; ++index) {
         skateSorter.push([index,0]);
      }
      for (index = 0; index < helmetColumn; ++index) {
         helmetSorter.push([index,0]);
      }

      jQuery("#player_roster_stick .sticky-table").tablesorter({
         sortList: stickSorter
      });
      jQuery("#player_roster_glove .sticky-table").tablesorter({
         sortList: gloveSorter
      });
      jQuery("#player_roster_pants .sticky-table").tablesorter({
         sortList: pantsSorter
      });
      jQuery("#player_roster_skate .sticky-table").tablesorter({
         sortList: skateSorter
      });
      jQuery("#player_roster_helmet .sticky-table").tablesorter({
         sortList: helmetSorter
      });



    }
);


~~~~~
