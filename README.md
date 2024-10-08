# readme1
test papers
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def salary_calculator():
    if request.method == 'POST':
        gross_salary = float(request.form['gross_salary'])
        tax_rate = float(request.form['tax_rate']) / 100
        net_salary = gross_salary * (1 - tax_rate)
        return render_template('index.html', net_salary=net_salary)

    return render_template('index.html', net_salary=None)

if __name__ == '__main__':
    app.run(debug=True)
