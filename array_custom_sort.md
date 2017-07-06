Here's a fun one.

This function returns an array, but we need it a custom array:
~~~~~

$result = playerEquipment($view->result[0]->field_field_player_equipment[0]['raw']['value']);


Array
(
    [Glove] => Array
        (
            [Warrior] => QRL
        )

    [Helmet] => Array
        (
            [Bauer] =>
        )

    [Pants] => Array
        (
            [Warrior] =>
        )

    [Skates] => Array
        (
            [Bauer] => Nexus 1N
        )

    [Stick] => Array
        (
            [Bauer] => Other
        )

)


$reorderedArray = array_merge(array_flip(array('Stick', 'Helmet', 'Glove', 'Skates', 'Pants')), $result);

~~~~~
