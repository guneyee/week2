use std::io::{self, Write};

enum Operation {
    Add,
    Subtract,
    Multiply,
    Divide,
}

fn calculate(operation: Operation, first_number: f64, second_number: f64) -> f64 {
    match operation {
        Operation::Add => first_number + second_number,
        Operation::Subtract => first_number - second_number,
        Operation::Multiply => first_number * second_number,
        Operation::Divide => first_number / second_number,
    }
}

fn main() {

    
    print!("Welcome to calculator");
    print!("-------");

    print!("Enter the numbers and the operation (e.g., 5 + 3): ");
    io::stdout().flush().unwrap();
    let mut input = String::new();
    io::stdin().read_line(&mut input).unwrap();
    let mut parts = input.trim().split_whitespace();

    let first_number: f64 = parts.next().unwrap().parse().unwrap();
    let operation_str: &str = parts.next().unwrap();
    let second_number: f64 = parts.next().unwrap().parse().unwrap();

    let operation = match operation_str {
        "+" => Operation::Add,
        "-" => Operation::Subtract,
        "*" => Operation::Multiply,
        "/" => Operation::Divide,
        _ => panic!("Invalid operation"),
    };

    let result = calculate(operation, first_number, second_number);
    println!("Result: {}", result);
}

