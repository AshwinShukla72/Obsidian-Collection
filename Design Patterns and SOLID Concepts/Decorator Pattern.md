
```TS
interface ActionFigure {
  getDescription: () => string,
  getCost: () => number,
}

class BasicActionFigure implements ActionFigure {
  getDescription(): string {
    return "Basic Action Figure";
  }
  getCost(): number {
    return 10
  }
}

abstract class ActionFigureDecorator implements ActionFigure {
  protected actionFigure: ActionFigure
  constructor(actionFigure: ActionFigure) {
    this.actionFigure = actionFigure;
  }
  abstract getDescription(): string;
  abstract getCost(): number;
}

class HatDecorator extends ActionFigureDecorator {

  getDescription(): string {
    return `${this.actionFigure.getDescription()} with a Hat`;
  }

  getCost(): number {
    return this.actionFigure.getCost() + 5; // The hat costs $5
  }
}

class ShieldDecorator extends ActionFigureDecorator {


  getDescription(): string {
    return `${this.actionFigure.getDescription()}, with a Shield`;
  }

  getCost(): number {
    return this.actionFigure.getCost() + 7; // The shield costs $7
  }
}

let myActionFigure = new BasicActionFigure();
console.log(myActionFigure.getDescription()); // Basic Action Figure
console.log(myActionFigure.getCost()); // 10

myActionFigure = new HatDecorator(myActionFigure);
console.log(myActionFigure.getDescription()); // Basic Action Figure, with a Hat
console.log(myActionFigure.getCost()); // 15

myActionFigure = new ShieldDecorator(myActionFigure);
console.log(myActionFigure.getDescription()); // Basic Action Figure, with a Hat, with a Shield
console.log(myActionFigure.getCost()); // 22
```