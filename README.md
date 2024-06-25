#include <iostream>
#include <vector>
#include <cmath>

void linearApproximation(const std::vector<double>& x, const std::vector<double>& y) {
    setlocale(LC_ALL, "Russian");
    int n = x.size();

    double sumX = 0, sumY = 0, sumXY = 0, sumXSquare = 0;

    for (int i = 0; i < n; i++) {
        sumX += x[i];
        sumY += y[i];
        sumXY += x[i] * y[i];
        sumXSquare += x[i] * x[i];
    }

    double meanX = sumX / n;
    double meanY = sumY / n;

    double a = (n * sumXY - sumX * sumY) / (n * sumXSquare - sumX * sumX);
    double b = meanY - a * meanX;

    std::cout << "Уравнение линейной аппроксимации: y = " << a << "x + " << b << std::endl;
}

int main() {
    setlocale(LC_ALL, "Russian");

    int length;
    std::cout << "Введите длину последовательности X: ";
    std::cin >> length;

    std::vector<double> x;
    for (int i = 1; i <= length; i++) {
        x.push_back(i);
    }

    std::vector<double> y;

    std::cout << "Введите значения для Y:" << std::endl;
    double inputY;
    for (int i = 0; i < length; i++) {
        std::cin >> inputY;
        y.push_back(inputY);
    }

    linearApproximation(x, y);

    return 0;
}
