Here's a fun one.

This function returns an array:
~~~~~

$result = playerEquipment($view->result[0]->field_field_player_equipment[0]['raw']['value']);

~~~~~
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

Which is all and good, accept it needs to be in a new order

~~~~~

$reorderedArray = array_merge(array_flip(array('Stick', 'Helmet', 'Glove', 'Skates', 'Pants')), $result);

~~~~~
