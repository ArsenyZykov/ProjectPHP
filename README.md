<?php

class Point {
    public $x;
    public $y;

    public function __construct($x = 0, $y = 0) {
        $this->x = $x;
        $this->y = $y;
    }

    public function moveX($distance) {
        $this->x += $distance;
    }

    public function moveY($distance) {
        $this->y += $distance;
    }

    public function moveByVector(Vector $vector) {
        $this->x += $vector->x;
        $this->y += $vector->y;
    }

    public function displayPosition() {
        echo "Точка находится в ($this->x, $this->y)\n";
    }
}

class Vector {
    public $x;
    public $y;

    public function __construct($x = 0, $y = 0) {
        $this->x = $x;
        $this->y = $y;
    }

    public function length() {
        return sqrt($this->x**2 + $this->y**2);
    }

    public function isZero() {
        return $this->x == 0 && $this->y == 0;
    }

    public function isPerpendicularTo(Vector $other) {
        return ($this->x * $other->x + $this->y * $other->y) == 0;
    }
}

$T1 = new Point(2, 5);
echo "T1: ";
$T1->displayPosition();

$V1 = new Vector(3, 4);
echo "Длина V1: " . $V1->length() . "\n";

$V2 = new Vector();
echo "Длина V2: " . $V2->length() . "\n";
echo "V2 нулевой вектор? " . ($V2->isZero() ? "Да" : "Нет") . "\n";

$V3 = new Vector(-4, 3);
echo "Длина V3: " . $V3->length() . "\n";
echo "V1 и V3 перпендикулярны? " . ($V1->isPerpendicularTo($V3) ? "Да" : "Нет") . "\n";

$T1->moveByVector($V1);
echo "Позиция T1 после переноса на V1: ";
$T1->displayPosition();

?>
