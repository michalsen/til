Augmenting a search term on categories from a drop down field

~~~~~

/**
 *
 *  Implements hook_search_api_query_alter()
 */
function my_module_search_api_query_alter($query) {
  // If category is chosen, we need to add a filter
  if ($_REQUEST['category'] != 'all') {

    // We need to create an array of children tids from the chosen category
    $children = taxonomy_get_tree($vid, $_REQUEST['category']);
      foreach ($children as $key => $value) {
        $tids[] = $value->tid;
      }

    // And create a filter for the items in that taxonomy array
    $filter = $query->createFilter('AND');
    $filter->condition('field_category_id', $tids, 'IN');
    $query->filter($filter);

  }
}

~~~~~
