package coverage

import (
	"os"
	"testing"
	"time"
	"sort"
	"errors"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func TestPeopleZeroLen(t *testing.T) {
	var p1 People = People{}

	expect := 0
	r := p1.Len()
	if r != expect {
		t.Errorf("Expected: %d, got %d", expect, r)
	}
}

func TestPeopleLen(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now()}

	var p1 People = People{a1, a2}

	expect := 2
	r := p1.Len()
	if r != expect {
		t.Errorf("Expected: %d, got %d", expect, r)
	}
}

func TestPeopleSwap(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now()}

	var p1 People = People{a1, a2}

	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}

	p1.Swap(0, 1)

	if p1[0] != a2 {
		t.Errorf("Expected a2 object")
	}
	if p1[1] != a1 {
		t.Errorf("Expected a1 object")
	}
}

func TestPeopleLessBirthDay(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now().Add(time.Second*time.Duration(1))}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now()}

	var p1 People = People{a1, a2}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}
}

func TestPeopleLessBirthDay2(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now().Add(time.Second*time.Duration(1))}

	var p1 People = People{a1, a2}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a2 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a1 {
		t.Errorf("Expected a2 object")
	}
}

func TestPeopleLessFirstName(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now()}

	var p1 People = People{a1, a2}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}
}
func TestPeopleLessFirstName2(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A2", lastName: "B1", birthDay:  time.Now()}

	var p1 People = People{a2, a1}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}
}

func TestPeopleLessLastName(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A1", lastName: "B2", birthDay:  time.Now()}

	var p1 People = People{a1, a2}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}
}

func TestPeopleLessLastName2(t *testing.T) {
	var a1 Person = Person{firstName: "A1", lastName: "B1", birthDay:  time.Now()}
	var a2 Person = Person{firstName: "A1", lastName: "B2", birthDay:  time.Now()}

	var p1 People = People{a2, a1}
	sort.Slice(p1, func(i, j int) bool {
		return p1.Less(i, j)
	})
	if p1[0] != a1 {
		t.Errorf("Expected a1 object")
	}
	if p1[1] != a2 {
		t.Errorf("Expected a2 object")
	}
}

func TestMatrixCreation(t *testing.T) {
	const strErr1 = "Rows need to be the same length"

	cases := map[string]struct {
		mtx 			string
		expectedRows	int
		expectedCols	int
		expErr			error
	}{
		"base creation 1": {
			mtx:			"1",
			expectedRows:   1,
			expectedCols:	1,
			expErr:			nil,
		},
		"base creation 2": {
			mtx:			"1 2\n3 4",
			expectedRows:   2,
			expectedCols:	2,
			expErr:			nil,
		},
		"base creation 3": {
			mtx:			"1 2\n3 4\n5 6",
			expectedRows:   3,
			expectedCols:	2,
			expErr:			nil,
		},
		"base creation 4": {
			mtx:			"1 2 3\n4 5 6",
			expectedRows:   2,
			expectedCols:	3,
			expErr:			nil,
		},
		"bad cols count 1": {
			mtx:			"1 2\n4 5 6",
			expectedRows:   0,
			expectedCols:	0,
			expErr:			errors.New(strErr1),
		},
		"bad cols count 2": {
			mtx:			"1 2 3\n5 6",
			expectedRows:   0,
			expectedCols:	0,
			expErr:			errors.New(strErr1),
		},
		"bad cols count 3": {
			mtx:			"\n5 6",
			expectedRows:   0,
			expectedCols:	0,
			expErr:			errors.New("strconv.Atoi: parsing \"\": invalid syntax"),
		},
	}

	for name, tt := range cases {
		t.Run(name, func(t *testing.T) {
			mtx, e := New(tt.mtx)
			
			if tt.expErr != nil {
				if e == nil {
					t.Errorf("expect error %s got nil", tt.expErr.Error())
				} else {
					if e.Error() != tt.expErr.Error() {
						t.Errorf("%s:\n wrong error is used in the return: got %s, want %s", name, e.Error(), tt.expErr.Error())
					}
				}
				return
			}
			if e != nil {
				t.Errorf("%s: expect no errors got %s", name, e.Error())
				return
			}

			if mtx.rows != tt.expectedRows {
				t.Errorf("expected rows: %d received %d", tt.expectedRows, mtx.rows)
			}
			if mtx.cols != tt.expectedCols {
				t.Errorf("expected cols: %d received %d", tt.expectedCols, mtx.cols)
			}
		})
	}
}

func TestMatrixFunctionRows(t *testing.T) {
	cases := map[string]struct {
		mtx 	string
		values	[][]int
	}{
		"test rows 1": {
			mtx:			"1",
			values:			[][]int{{1},},
		},
		"test rows 2": {
			mtx:			"1 2\n3 4",
			values:			[][]int{{1, 2}, {3, 4},},
		},
		"test rows 3": {
			mtx:			"1 2\n3 4\n5 6",
			values:			[][]int{{1, 2}, {3, 4}, {5, 6}},
		},
		"test rows 4": {
			mtx:			"1 2 3\n4 5 6",
			values:			[][]int{{1, 2, 3}, {4, 5, 6}},
		},
	}

	for name, tt := range cases {
		t.Run(name, func(t *testing.T) {
			mtx, e := New(tt.mtx)
			if e != nil {
				t.Errorf("%s: expect no errors got %s", name, e.Error())
				return
			}
			
			rows := mtx.Rows()

			if len(rows) != len(tt.values) {
				t.Errorf("%s: expected rows len: %d received row len: %d", name, len(rows), len(tt.values))
				return
			}
			if len(rows[0]) != len(tt.values[0]) {
				t.Errorf("%s: expected cols len: %d received cols len: %d", name, len(rows[0]), len(tt.values[0]))
				return
			}

			for i := 0; i < len(tt.values); i++ {
				for j := 0; j < len(tt.values[0]); j++ {
					if rows[i][j] != tt.values[i][j] {
						t.Errorf("%s: expected value [%d][%d]: %d, received: %d", name, i, j, tt.values[i][j], rows[i][j])
					}
				}
			}
		})
	}
}

func TestMatrixFunctionCols(t *testing.T) {
	cases := map[string]struct {
		mtx 	string
		values	[][]int
	}{
		"test cols 1": {
			mtx:			"1",
			values:			[][]int{{1},},
		},
		"test cols 2": {
			mtx:			"1 2\n3 4",
			values:			[][]int{{1, 3}, {2, 4},},
		},
		"test cols 3": {
			mtx:			"1 2\n3 4\n5 6",
			values:			[][]int{{1, 3, 5}, {2, 4, 6}},
		},
		"test cols 4": {
			mtx:			"1 2 3\n4 5 6",
			values:			[][]int{{1, 4}, {2, 5}, {3, 6}},
		},
	}

	for name, tt := range cases {
		t.Run(name, func(t *testing.T) {
			mtx, e := New(tt.mtx)
			if e != nil {
				t.Errorf("%s: expect no errors got %s", name, e.Error())
				return
			}
			
			cols := mtx.Cols()

			if len(cols) != len(tt.values) {
				t.Errorf("%s: expected rows len: %d received row len: %d", name, len(cols), len(tt.values))
				return
			}
			if len(cols[0]) != len(tt.values[0]) {
				t.Errorf("%s: expected cols len: %d received cols len: %d", name, len(cols[0]), len(tt.values[0]))
				return
			}

			for i := 0; i < len(tt.values); i++ {
				for j := 0; j < len(tt.values[0]); j++ {
					if cols[i][j] != tt.values[i][j] {
						t.Errorf("%s: expected value [%d][%d]: %d, received: %d", name, i, j, tt.values[i][j], cols[i][j])
					}
				}
			}
		})
	}
}

func TestMatrixFunctionSet(t *testing.T) {
	cases := map[string]struct {
		mtx 	string
		idx		[][]int
		values	[]int
		result	[][]int
	}{
		"test set 1": {
			mtx:			"0 0\n0 0",
			idx:			[][]int{{0, 0}, {0, 1}, {1, 0}, {1, 1},},
			values:			[]int{1, 2, 3, 4},
			result:			[][]int{{1, 2}, {3, 4}},
		},
		"test set 2": {
			mtx:			"0 0 0\n0 0 0",
			idx:			[][]int{{0, 0}, {0, 1}, {0, 2}, {1, 0}, {1, 1}, {1, 2},},
			values:			[]int{1, 2, 3, 4, 5, 6},
			result:			[][]int{{1, 2, 3}, {4, 5, 6}},
		},
		"test set 3": {
			mtx:			"0 0\n0 0\n0 0",
			idx:			[][]int{{0, 0}, {0, 1}, {1, 0}, {1, 1}, {2, 0}, {2, 1},},
			values:			[]int{1, 2, 3, 4, 5, 6},
			result:			[][]int{{1, 2}, {3, 4}, {5, 6}},
		},
	}

	for name, tt := range cases {
		t.Run(name, func(t *testing.T) {
			mtx, e := New(tt.mtx)
			if e != nil {
				t.Errorf("%s: expect no errors got %s", name, e.Error())
				return
			}
			
			for i := 0; i < len(tt.idx); i++ {
				ret := mtx.Set(tt.idx[i][0], tt.idx[i][1], tt.values[i])
				if !ret {
					t.Errorf("%s: unexpected ret==false [%d]", name, i)
					return
				}
			}

			rows := mtx.Rows()

			if len(rows) != len(tt.result) {
				t.Errorf("%s: expected rows len: %d received row len: %d", name, len(rows), len(tt.result))
				return
			}
			if len(rows[0]) != len(tt.result[0]) {
				t.Errorf("%s: expected cols len: %d received cols len: %d", name, len(rows[0]), len(tt.result[0]))
				return
			}

			for i := 0; i < len(tt.result); i++ {
				for j := 0; j < len(tt.result[0]); j++ {
					if rows[i][j] != tt.result[i][j] {
						t.Errorf("%s: expected value [%d][%d]: %d, received: %d", name, i, j, tt.result[i][j], rows[i][j])
					}
				}
			}
		})
	}
}

func TestMatrixFunctionSetRetFalse(t *testing.T) {
	cases := map[string]struct {
		mtx 	string
		idx		[][]int
	}{
		"test set false 1": {
			mtx:			"0 0\n0 0",
			idx:			[][]int{{-1, 0}, {0, -1}, {2, 0}, {2, 2}},
		},
		"test set false 2": {
			mtx:			"0 0 0\n0 0 0",
			idx:			[][]int{{-1, -1}, {3, 0}, {0, 3}, {3, 3}},
		},
		"test set false 3": {
			mtx:			"0 0\n0 0\n0 0",
			idx:			[][]int{{-1, 0}, {-1, -1}, {3, 0}, {0, 3}, {3, 3}},
		},
	}

	for name, tt := range cases {
		t.Run(name, func(t *testing.T) {
			mtx, e := New(tt.mtx)
			if e != nil {
				t.Errorf("%s: expect no errors got %s", name, e.Error())
				return
			}
			
			for i := 0; i < len(tt.idx); i++ {
				ret := mtx.Set(tt.idx[i][0], tt.idx[i][1], -1)
				if ret {
					t.Errorf("%s: unexpected ret==true case [%d] idx [%d][%d]", name, i, tt.idx[i][0], tt.idx[i][1])
				}
			}
		})
	}
}
