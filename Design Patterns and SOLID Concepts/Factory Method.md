```ad-info
A creational design pattern that provides an interface for creating objects ina superclass, but allows subclasses to alter the type of object that will be created.
```

Implementation of Factory method for benders
```TS
enum Nations {
  Fire = "Fire Nation",
  Water = "Water Tribe",
  Earth = "Earth Kingdom",
  Air = "Air Nomads",
  Metal = "Earth Kingdom",
}

type Elements = "Fire" | "Water" | "Earth" | "Air" | "Metal";

enum OriginalBenders {
  Fire = "Dragon",
  Water = "Moon",
  Air = "Flying Bison",
  Earth = "Badger Mole",
  Metal = "Toph Beifong"
}

interface BenderInterface {
  nation: Nations;
  element: Elements;
  originalBender: OriginalBenders;
  bend: () => void;
  getBenderInfo: () => unknown;
}

export class Bender implements BenderInterface {
  name: string;
  nation: Nations;
  element: Elements;
  originalBender: OriginalBenders;

  constructor(name: string, nation: Nations, element: Elements, originalBender: OriginalBenders) {
    this.name = name;
    this.nation = nation;
    this.element = element;
    this.originalBender = originalBender;
  }

  bend(): void {
    console.log(`${this.name} does ${this.element} bending`);
  }

  getBenderInfo(): Omit<BenderInterface, 'getBenderInfo' | 'bend'> & { name: string } {
    const { name, nation, element, originalBender } = this;
    return {
      name,
      nation,
      element,
      originalBender
    };
  }
}

export class FireBender extends Bender {
  constructor(name: string) {
    super(name, Nations.Fire, "Fire", OriginalBenders.Fire);
  }
}

export class EarthBender extends Bender {
  constructor(name: string) {
    super(name, Nations.Earth, "Earth", OriginalBenders.Earth);
  }
}

export class WaterBender extends Bender {
  constructor(name: string) {
    super(name, Nations.Water, "Water", OriginalBenders.Water);
  }
}

export class AirBender extends Bender {
  constructor(name: string) {
    super(name, Nations.Air, "Air", OriginalBenders.Air);
  }
}
export class MetalBender extends EarthBender {
  constructor(name: string) {
    super(name)
    this.element = 'Metal'
    this.originalBender = OriginalBenders.Metal
  }
}
export default class BendersFactory {
  createBender(name: string, element: Elements): Bender {
    switch (element) {
      case "Fire":
        return new FireBender(name);
      case "Earth":
        return new EarthBender(name);
      case "Water":
        return new WaterBender(name);
      case "Air":
        return new AirBender(name);
      case "Metal":
        return new MetalBender(name)
      default:
        throw new Error("Invalid element");
    }
  }
}

const earthBender = new BendersFactory().createBender("Toph", "Earth")
console.log(earthBender)
const metalBender = new BendersFactory().createBender("Lin Beifong", "Metal")
console.log(metalBender)
```