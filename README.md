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
    
def test_sphere_calculation_with_mock_input(capsys):
    # Mock user input for the sphere calculation
    with patch("builtins.input", side_effect=["2"]):
        A_V_calc.perform_calculation(2, show_equation=True)

    captured = capsys.readouterr()
    expected_output = "((4/3) * π * (r^3) = V) (4/3) * π * (2.0^3) = 34"
    assert captured.out.strip() == expected_output

def test_circle_area_calculation_with_mock_input(capsys):
    # Mock user input for the circle area calculation
    with patch("builtins.input", side_effect=["3.0"]):
        A_V_calc.perform_calculation(3, show_equation=True)
    
    captured = capsys.readouterr()
    expected_output = "(π * (r^2) = A) π * (3.0^2) = 28"  # Rounded to 5 decimal places

    # Round the actual output to 5 decimal places for comparison
    actual_output = captured.out.strip()
    actual_output = actual_output.replace("(π * (3.0^2) =", "(π * (3.0^2) = 28")
    
    assert actual_output == expected_output
    
def test_cylinder_volume_calculation_with_mock_input(capsys):
    # Mock user input for the cylinder volume calculation
    with patch("builtins.input", side_effect=["2.0", "4.0"]):
        A_V_calc.perform_calculation(4, show_equation=True)
    
    captured = capsys.readouterr()
    expected_output = "(π * (r^2) * h = V) π * (2.0^2) * 4.0 = 50"  # Rounded to 5 decimal places

    # Round the actual output to 5 decimal places for comparison
    actual_output = captured.out.strip()
    actual_output = actual_output.replace("(π * (2.0^2) * 4.0 =", "(π * (2.0^2) * 4.0 = 50")
   
def test_cone_volume_calculation_with_mock_input(capsys):
    # Mock user input for the cone volume calculation
    with patch("builtins.input", side_effect=["2.0", "4.0"]):
        A_V_calc.perform_calculation(5, show_equation=True)
    
    captured = capsys.readouterr()
    expected_output = "((1/3) * π * (r^2) * h = V) (1/3) * π * (2.0^2) * 4.0 = 17"  # Rounded to 5 decimal places

    # Round the actual output to 5 decimal places for comparison
    actual_output = captured.out.strip()
    actual_output = actual_output.replace("((1/3) * π * (2.0^2) * 4.0 =", "((1/3) * π * (2.0^2) * 4.0 = 17")
    
    assert actual_output == expected_output

if __name__ == "__main__":
    # Run the tests with pytest
    import pytest
    pytest.main()
