# -DGFN-2-Assgn-1-2023
# Joshua Arbuckle
# sourced from ChatGPT asked it to use my def perform_calculation statment to make a pytest code for me
import A_V_calc
from unittest.mock import patch

def test_rectangle_calculation_with_mock_input(capsys):
    # Mock user input for the rectangle calculation
    with patch("builtins.input", side_effect=["2.0", "3.0"]):
        A_V_calc.perform_calculation(1, show_equation=True)
    
    captured = capsys.readouterr()
    expected_output = "(x * y = z) 2.0 * 3.0 = 6.0"
    assert captured.out.strip() == expected_output
    
if __name__ == "__main__":
    # Run the tests with pytest
    import pytest
    pytest.main()
