CREATE TABLE tavern (
  tavernID INT IDENTITY(1,1),
  tavernName VARCHAR(255),
  locationID INT,
  ownerID INT,
  ratsID INT,
  servicesID INT,
  PRIMARY KEY (tavernID),
  FOREIGN KEY (locationID) REFERENCES locations(locationID),
  FOREIGN KEY (ownerID) REFERENCES owners(ownerID),
  FOREIGN KEY (ratsID) REFERENCES rats(ratsID)
  FOREIGN KEY (servicesID) REFERENCES services(servicesID)
);

INSERT INTO tavern (tavernID, tavernName, locationID, ownerID, ratsID, serviceID)
VALUES ('redwig',1,1,1,1),
        ('charlies',2,2,3,1),
        ('bobs',2,3,1,3),
        ('hammerfell',2,4,2,1),
        ('ringos', 4,3,2,1);

CREATE TABLE owners (
  ownerID INT IDENTITY(1,1),
  ownerName VARCHAR(25)
  roleID INT,
  PRIMARY KEY (ownerID),
  FOREIGN KEY (roleID) REFERENCES roles(roleID)
);

INSERT INTO owners (ownerName, rollID,)
VALUES ('Ned',1),
        ('Don',3),
        ('Forkas',4),
        ('Murial',4),
        ('Geralt',3);


CREATE TABLE roles (
  roleID INT IDENTITY(1,1),
  roleName VARCHAR(25),
  roleDescription VARCHAR(100),
  PRIMARY KEY (roleID)
);

INSERT INTO roles (roleName, roleDescription)
VALUES ('warrior', 'skilled in combat uses melee weapons'),
        ('dragon', 'mythical beast'),
        ('archer', 'skilled with a bow'),
        ('thief', 'experienced with tricker and thieving'),
        ('samurai', 'warrior in search of the number 1 headband');



CREATE TABLE locations (
  locationID INT IDENTITY(1,1),
  locationName VARCHAR(100);
);

INSERT INTO locations (locationName)
VALUES ('Briarwood'),
        ('Compton'),
        ('Skyrim'),
        ('Reach'),
        ('Naboo');

CREATE TABLE rats (
  ratsID INT IDENTITY(1,1),
  ratNames VARCHAR(50),
  tavernID INT,
  PRIMARY KEY (ratsID),
  FOREIGN KEY (tavernID) REFERENCES taverns(tavernID)
);

INSERT INTO rats (ratNames, tavernID,)
VALUES ('carl', 3),
        ('dan', 2),
        ('goku', 1),
        ('rangiku', 1);

CREATE TABLE services (
  servicesID INT IDENTITY(1,1),
  serviceName VARCHAR(100),
  statusID INT,
  dateRcvd DATE,
  PRIMARY KEY (servicesID),
  FOREIGN KEY (statusID) REFERENCES statuses(statusID)
);

INSERT INTO services (serviceName, statusID, dateRcvd)
VALUES ('gunsmithing',3, DATE),
       ('swordsmithing',2, DATE),
       ('enchanting', 1, DATE),
       ('alchemy', 4, DATE),
       ('wizadry',1, DATE);

CREATE TABLE serviceStat (
statusID INT IDENTITY(1,1),
serviceName VARCHAR(100),
statusName VARCHAR(100),
PRIMARY KEY (statusID),
FOREIGN KEY (serviceName) REFERENCES servicesName(serviceName)
);

INSERT INTO serviceStat ( serviceName, statusName)
VALUES ('gunsmithing', 'active'),
        ('gunsmithing', 'inactive'),
        ('alchemy', 'active'),
        ('wizadry', 'inactive'),
        ('enchanting', 'inactive');

CREATE TABLE sales (
  salesID INT IDENTITY(1,1),
  serviceID INT,
  tavernID INT,
  guest VARCHAR(100),
  price DECIMAL(6,2),
  datePurchased DATE,
  amountPurchased INT
  PRIMARY KEY (salesID),
  FOREIGN KEY (tavernID) REFERENCES taverns(tavernID),
  FOREIGN KEY (serviceID) REFERENCES services(serviceID)
);

INSERT INTO sales (serviceID, tavernID, guest, price, datePurchased, amountPurchased)
VALUES(5,3, 'chad', 23.2, DATE, 20),
      (1,5, 'lewis', 27.4, DATE, 5),
      (3,3, 'mark', 17, DATE, 2),
      (1,1, 'lenny', 12.4, DATE, 1)
      (5,4, 'sammy', 13, DATE,4); 

CREATE TABLE supplies (
  supplyID INT IDENTITY(1,1),
  tavernID INT,
  supplyName VARCHAR(100),
  unit VARCHAR (3),
  price DECIMAL (6,2)
  updatedDate DATE,
  quantity INT,
  PRIMARY KEY (supplyID),
  FOREIGN KEY (tavernID) REFERENCES taverns(tavernID)
);

INSERT INTO supplies (tavernID, supplyName, unit, price, updatedDate, quantity)
VALUES(3, 'ale', 'lbs', 5, DATE, 1),
      (4, 'wine', 'oz', 5.2, DATE, 3),
      (1, 'mutton','lbs', 17, DATE, 2),
      (2, 'lamb', 'lbs', 13, DATE, 5),
      (5, 'mead', 'oz', 15, DATE, 3);