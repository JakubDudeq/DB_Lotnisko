CREATE DATABASE IF NOT EXISTS europejskie_linie_lotnicze
DEFAULT CHARSET=utf8mb4
COLLATE=utf8mb4_unicode_ci;
USE  europejskie_linie_lotnicze;

CREATE TABLE IF NOT EXISTS `kraje` (
  `ID_Kraj` int(11) NOT NULL,
  `Kraj` varchar(20) NOT NULL
);

CREATE TABLE IF NOT EXISTS `kraj-pasazer` (
  `ID_Kraju` int(11) NOT NULL,
  `ID_Pasazera` int(11) NOT NULL
);


CREATE TABLE IF NOT EXISTS `linie_lolnicze` (
  `ID_Linia` int(11) NOT NULL,
  `Nazwa` varchar(20) NOT NULL,
  `kraj` int(11) DEFAULT NULL
);


CREATE TABLE IF NOT EXISTS `lot` (
  `ID_Lotu` int(11) NOT NULL,
  `Ilosc_Pasazerow` int(7) UNSIGNED NOT NULL DEFAULT 0,
  `Linia_Lotnicza` int(11) DEFAULT NULL,
  `Miasto_Wylotu` int(11) DEFAULT NULL,
  `Miasto_Przylotu` int(11) DEFAULT NULL,
  `Data` timestamp NOT NULL DEFAULT current_timestamp(),
  `Pilot` int(11) NOT NULL,
  `Status_Odlotu` int(11) DEFAULT NULL,
  `ID_Statusu` int(11) DEFAULT NULL
);

CREATE TABLE IF NOT EXISTS `lot-pasazer` (
  `ID_Pasazera` int(11) NOT NULL,
  `ID_Lotu` int(11) NOT NULL
);

CREATE TABLE IF NOT EXISTS `lotniska` (
  `ID_Lotniska` int(11) NOT NULL,
  `Miasto` varchar(20) NOT NULL,
  `kraj` int(11) DEFAULT NULL
);

CREATE TABLE IF NOT EXISTS `statusy_odlotu` (
  `ID_Statusu` int(11) NOT NULL,
  `Status` varchar(11) NOT NULL
);


CREATE TABLE IF NOT EXISTS `pasazer` (
  `ID_Pasazera` int(11) NOT NULL,
  `Imie` varchar(20) NOT NULL,
  `Nazwisko` varchar(30) NOT NULL,
  `Data_Urodzenia` date NOT NULL
);

CREATE TABLE IF NOT EXISTS `pilot` (
  `ID_Pilota` int(11) NOT NULL,
  `Imie` varchar(20) NOT NULL,
  `Nazwisko` varchar(30) NOT NULL,
  `Wiek` date NOT NULL
);

RENAME TABLE `linie_lolnicze` TO `linie_lotnicze`;

INSERT INTO `kraj-pasazer` (`ID_Kraju`, `ID_Pasazera`) VALUES
(1, 1),
(1, 2),
(1, 3),
(2, 4),
(2, 5),
(3, 6),
(3, 7),
(4, 8),
(4, 9),
(5, 10),
(5, 11),
(6, 12),
(6, 13),
(7, 14),
(7, 15),
(8, 16),
(8, 17),
(9, 18),
(9, 19),
(10, 20),
(10, 21),
(11, 22),
(11, 23),
(12, 24),
(12, 25),
(13, 26),
(13, 27),
(14, 28),
(14, 29),
(15, 30);

INSERT INTO `kraje` (`ID_Kraj`, `Kraj`) VALUES
(1, 'Albania'),
(2, 'Andora'),
(3, 'Austria'),
(4, 'Białoruś'),
(5, 'Belgia'),
(6, 'Bośnia i Hercegowina'),
(7, 'Bułgaria'),
(8, 'Chorwacja'),
(9, 'Czarnogóra'),
(10, 'Czechy'),
(11, 'Dania'),
(12, 'Estonia'),
(13, 'Finlandia'),
(14, 'Francja'),
(15, 'Grecja'),
(16, 'Hiszpania'),
(17, 'Holandia'),
(18, 'Irlandia'),
(19, 'Islandia'),
(20, 'Liechtenstein'),
(21, 'Litwa'),
(22, 'Luksemburg'),
(23, 'Łotwa'),
(24, 'Macedonia Północna'),
(25, 'Malta'),
(26, 'Moldawia'),
(27, 'Monako'),
(28, 'Niemcy'),
(29, 'Norwegia'),
(30, 'Polska'),
(31, 'Portugalia'),
(32, 'Rosja'),
(33, 'Rumunia'),
(34, 'San Marino'),
(35, 'Serbia'),
(36, 'Słowacja'),
(37, 'Słowenia'),
(38, 'Szwajcaria'),
(39, 'Szwecja'),
(40, 'Turcja'),
(41, 'Ukraina'),
(42, 'Watykan'),
(43, 'Węgry'),
(44, 'Wielka Brytania'),
(45, 'Włochy');


INSERT INTO `linie_lotnicze` (`ID_Linia`, `Nazwa`, `kraj`) VALUES
(1, 'LOT Polish Airlines', 30),
(2, 'Lufthansa', 28),
(3, 'British Airways', 44),
(4, 'Air France', 14),
(5, 'KLM', 17),
(6, 'Iberia', 15),
(7, 'Scandinavian Airline', 38),
(8, 'Ryanair', 24),
(9, 'EasyJet', 14),
(10, 'Turkish Airlines', 40),
(11, 'Aer Lingus', 18),
(12, 'Finnair', 13),
(13, 'Swiss International ', 38),
(14, 'Alitalia', 45),
(15, 'Norwegian Air Shuttl', 29),
(16, 'Austrian Airlines', 3);

INSERT INTO `lot` (`ID_Lotu`, `Ilosc_Pasazerow`, `Linia_Lotnicza`, `Miasto_Wylotu`, `Miasto_Przylotu`, `Data`, `Pilot`, `Status_Odlotu`, `ID_Statusu`) VALUES
(1, 7, 1, 4, 1, '2024-02-04 11:00:00', 1, 1, 2),
(2, 6, 2, 2, 10, '2024-02-05 13:30:00', 2, 2, 2),
(3, 6, 3, 15, 28, '2024-02-06 09:45:00', 3, 1, 1),
(4, 6, 1, 7, 23, '2024-02-07 07:15:00', 10, 2, 1),
(5, 6, 2, 11, 14, '2024-02-08 15:00:00', 13, 1, 1);

INSERT INTO `lot-pasazer` (`ID_Pasazera`, `ID_Lotu`) VALUES
(1, 1),
(2, 1),
(3, 1),
(4, 1),
(5, 1),
(6, 2),
(7, 2),
(8, 2),
(9, 2),
(10, 2),
(11, 3),
(12, 3),
(13, 3),
(14, 3),
(15, 3),
(16, 4),
(17, 4),
(18, 4),
(19, 4),
(20, 4),
(21, 5),
(22, 5),
(23, 5),
(24, 5),
(25, 5),
(26, 1),
(27, 2),
(28, 3),
(29, 4),
(30, 5),
(31, 1);

INSERT INTO `lotniska` (`ID_Lotniska`, `Miasto`, `kraj`) VALUES
(1, 'Skopje', 24),
(2, 'Paryż', 14),
(3, 'Berlin', 28),
(4, 'Londyn', 44),
(5, 'Madryt', 15),
(6, 'Rzym', 45),
(7, 'Amsterdam', 17),
(8, 'Wiedeń', 3),
(9, 'Praga', 10),
(10, 'Barcelona', 15),
(11, 'Zurych', 38),
(12, 'Oslo', 29),
(13, 'Sztokholm', 39),
(14, 'Lizbona', 31),
(15, 'Ateny', 16),
(16, 'Budapeszt', 33),
(17, 'Bruksela', 17),
(18, 'Kopenhaga', 11),
(19, 'Helsinki', 19),
(20, 'Luksemburg', 20),
(21, 'Dublin', 18),
(22, 'Bukareszt', 22),
(23, 'Warszawa', 30),
(24, 'Edynburg', 44),
(25, 'Lyon', 14),
(26, 'Neapol', 45),
(27, 'Kijów', 41),
(28, 'Hamburg', 28),
(29, 'Genewa', 39);

INSERT INTO `pasazer` (`ID_Pasazera`, `Imie`, `Nazwisko`, `Data_Urodzenia`) VALUES
(1, 'Jan', 'Kowalski', '1990-01-15'),
(2, 'Anna', 'Nowak', '1985-05-20'),
(3, 'Piotr', 'Wiśniewski', '1998-11-08'),
(4, 'Karolina', 'Zalewska', '1992-07-03'),
(5, 'Mateusz', 'Lis', '1980-09-12'),
(6, 'Agnieszka', 'Dąbrowska', '1995-03-28'),
(7, 'Marcin', 'Jaworski', '1987-12-05'),
(8, 'Magdalena', 'Kowalczyk', '1993-06-18'),
(9, 'Kamil', 'Zawadzki', '1984-02-22'),
(10, 'Dominika', 'Kaczmarek', '1997-08-07'),
(11, 'Bartosz', 'Szymański', '1991-04-11'),
(12, 'Natalia', 'Lewandowska', '1989-10-26'),
(13, 'Krzysztof', 'Pawlak', '1994-09-02'),
(14, 'Weronika', 'Michalak', '1986-07-14'),
(15, 'Patryk', 'Czarnecki', '2000-01-30'),
(16, 'Monika', 'Górka', '1996-04-25'),
(17, 'Łukasz', 'Jóźwiak', '1983-11-09'),
(18, 'Aleksandra', 'Tomczak', '1999-05-16'),
(19, 'Artur', 'Sikorski', '1988-08-01'),
(20, 'Karolina', 'Kubiak', '1992-12-17'),
(21, 'Rafał', 'Wróbel', '1981-06-21'),
(22, 'Marta', 'Olszewska', '1993-10-07'),
(23, 'Paweł', 'Witkowski', '1985-02-13'),
(24, 'Katarzyna', 'Cieślak', '1998-07-29'),
(25, 'Damian', 'Grabowski', '1987-03-04'),
(26, 'Alicja', 'Kowal', '1991-09-19'),
(27, 'Jakub', 'Wójcik', '1994-05-03'),
(28, 'Sylwia', 'Klimek', '1989-11-18'),
(29, 'Tomasz', 'Adamski', '1996-08-02'),
(30, 'Oliwia', 'Bąk', '1982-12-26'),
(31, 'Wojciech', 'Kozłowski', '1993-05-11');


INSERT INTO `pilot` (`ID_Pilota`, `Imie`, `Nazwisko`, `Wiek`) VALUES
(1, 'Adam', 'Nowak', '1990-01-15'),
(2, 'Ewa', 'Kowalska', '1985-05-20'),
(3, 'Piotr', 'Wiśniewski', '1998-11-08'),
(4, 'Karolina', 'Zalewska', '1992-07-03'),
(5, 'Mateusz', 'Lis', '1980-09-12'),
(6, 'Agnieszka', 'Dąbrowska', '1995-03-28'),
(7, 'Marcin', 'Jaworski', '1987-12-05'),
(8, 'Magdalena', 'Kowalczyk', '1993-06-18'),
(9, 'Kamil', 'Zawadzki', '1984-02-22'),
(10, 'Dominika', 'Kaczmarek', '1997-08-07'),
(11, 'Bartosz', 'Szymański', '1991-04-11'),
(12, 'Natalia', 'Lewandowska', '1989-10-26'),
(13, 'Krzysztof', 'Pawlak', '1994-09-02'),
(14, 'Weronika', 'Michalak', '1986-07-14'),
(15, 'Patryk', 'Czarnecki', '2000-01-30'),
(16, 'Monika', 'Górka', '1996-04-25'),
(17, 'Łukasz', 'Jóźwiak', '1983-11-09'),
(18, 'Aleksandra', 'Tomczak', '1999-05-16'),
(19, 'Artur', 'Sikorski', '1988-08-01'),
(20, 'Karolina', 'Kubiak', '1992-12-17');

INSERT INTO `statusy_odlotu` (`ID_Statusu`, `Status`) VALUES
(1, 'Przed wylot'),
(2, 'W trakcie l'),
(3, 'Po wylądowa'),
(4, 'Błąd danych');

DELIMITER $$

CREATE DEFINER=`root`@`localhost` FUNCTION `SprawdzPoprawnoscMiasta` (`MiastoWylotu` VARCHAR(255), `MiastoPrzylotu` VARCHAR(255)) RETURNS INT
    BEGIN
    DECLARE Status INT;

    IF MiastoWylotu = MiastoPrzylotu THEN
        SET Status = 4;
    ELSE
        SET Status = -1;
    END IF;
    RETURN Status;
END$$

CREATE TRIGGER `Trigger2` BEFORE UPDATE ON `lot` FOR EACH ROW BEGIN
    DECLARE Status INT;
    SET Status = SprawdzPoprawnoscMiasta(NEW.Miasto_Wylotu, NEW.Miasto_Przylotu);
    IF Status = 4 THEN
        SET NEW.ID_Statusu = Status;
    END IF;
END$$




CREATE TRIGGER `Trigger1` AFTER INSERT ON `lot-pasazer` FOR EACH ROW BEGIN
    UPDATE lot
    SET Ilosc_Pasazerow = (
        SELECT COUNT(*)
        FROM `lot-pasazer`
        WHERE ID_Lotu = NEW.ID_Lotu
    )
    WHERE ID_Lotu = NEW.ID_Lotu;
END$$
DELIMITER ;

ALTER TABLE `kraje`
ADD COLUMN `Ludnosc` int(11) DEFAULT 0;

UPDATE `kraje` SET `Ludnosc` = 5822763 WHERE `ID_Kraj` = 11;
UPDATE `kraje` SET `Ludnosc` = 1326535 WHERE `ID_Kraj` = 12;
UPDATE `kraje` SET `Ludnosc` = 5540720 WHERE `ID_Kraj` = 13;
UPDATE `kraje` SET `Ludnosc` = 67059887 WHERE `ID_Kraj` = 14;
UPDATE `kraje` SET `Ludnosc` = 10724599 WHERE `ID_Kraj` = 15;
UPDATE `kraje` SET `Ludnosc` = 46754783 WHERE `ID_Kraj` = 16;
UPDATE `kraje` SET `Ludnosc` = 17498000 WHERE `ID_Kraj` = 17;
UPDATE `kraje` SET `Ludnosc` = 4920455 WHERE `ID_Kraj` = 18;
UPDATE `kraje` SET `Ludnosc` = 356991 WHERE `ID_Kraj` = 19;
UPDATE `kraje` SET `Ludnosc` = 39732 WHERE `ID_Kraj` = 20;
UPDATE `kraje` SET `Ludnosc` = 2679465 WHERE `ID_Kraj` = 21;
UPDATE `kraje` SET `Ludnosc` = 634730 WHERE `ID_Kraj` = 22;
UPDATE `kraje` SET `Ludnosc` = 1901548 WHERE `ID_Kraj` = 23;
UPDATE `kraje` SET `Ludnosc` = 2073894 WHERE `ID_Kraj` = 24;
UPDATE `kraje` SET `Ludnosc` = 514564 WHERE `ID_Kraj` = 25;
UPDATE `kraje` SET `Ludnosc` = 2538918 WHERE `ID_Kraj` = 26;
UPDATE `kraje` SET `Ludnosc` = 38897 WHERE `ID_Kraj` = 27;
UPDATE `kraje` SET `Ludnosc` = 83149300 WHERE `ID_Kraj` = 28;
UPDATE `kraje` SET `Ludnosc` = 5391369 WHERE `ID_Kraj` = 29;
UPDATE `kraje` SET `Ludnosc` = 38437239 WHERE `ID_Kraj` = 30;
UPDATE `kraje` SET `Ludnosc` = 10276617 WHERE `ID_Kraj` = 31;
UPDATE `kraje` SET `Ludnosc` = 145912025 WHERE `ID_Kraj` = 32;
UPDATE `kraje` SET `Ludnosc` = 19286123 WHERE `ID_Kraj` = 33;
UPDATE `kraje` SET `Ludnosc` = 33785 WHERE `ID_Kraj` = 34;
UPDATE `kraje` SET `Ludnosc` = 7022268 WHERE `ID_Kraj` = 35;
UPDATE `kraje` SET `Ludnosc` = 5461100 WHERE `ID_Kraj` = 36;
UPDATE `kraje` SET `Ludnosc` = 2084301 WHERE `ID_Kraj` = 37;
UPDATE `kraje` SET `Ludnosc` = 8695582 WHERE `ID_Kraj` = 38;
UPDATE `kraje` SET `Ludnosc` = 10353456 WHERE `ID_Kraj` = 39;
UPDATE `kraje` SET `Ludnosc` = 82319724 WHERE `ID_Kraj` = 40;
UPDATE `kraje` SET `Ludnosc` = 41806216 WHERE `ID_Kraj` = 41;
UPDATE `kraje` SET `Ludnosc` = 8257 WHERE `ID_Kraj` = 42;
UPDATE `kraje` SET `Ludnosc` = 9630428 WHERE `ID_Kraj` = 43;
UPDATE `kraje` SET `Ludnosc` = 67886011 WHERE `ID_Kraj` = 44;
UPDATE `kraje` SET `Ludnosc` = 60461826 WHERE `ID_Kraj` = 45;


ALTER TABLE `kraj-pasazer`
  ADD KEY `Relacja10` (`ID_Pasazera`),
  ADD KEY `Relacja9` (`ID_Kraju`);

ALTER TABLE `kraje`
  ADD PRIMARY KEY (`ID_Kraj`);

ALTER TABLE `linie_lotnicze`
  ADD PRIMARY KEY (`ID_Linia`);

ALTER TABLE `lot`
  ADD PRIMARY KEY (`ID_Lotu`),
  ADD KEY `Relacja4` (`Status_Odlotu`),
  ADD KEY `Relacja1` (`Miasto_Przylotu`),
  ADD KEY `Relacja2` (`Miasto_Wylotu`),
  ADD KEY `Relacja3` (`Linia_Lotnicza`),
  ADD KEY `Relacja8` (`Pilot`),
  ADD KEY `Relacja12` (`ID_Statusu`);

ALTER TABLE `lot-pasazer`
  ADD KEY `Relacja 7` (`ID_Lotu`),
  ADD KEY `Relacja6` (`ID_Pasazera`);

ALTER TABLE `lotniska`
  ADD PRIMARY KEY (`ID_Lotniska`),
  ADD KEY `Relacja11` (`kraj`);

ALTER TABLE `pasazer`
  ADD PRIMARY KEY (`ID_Pasazera`),
  ADD KEY `index1` (`Imie`,`Nazwisko`);

ALTER TABLE `pilot`
  ADD PRIMARY KEY (`ID_Pilota`),
  ADD KEY `index2` (`Imie`,`Nazwisko`);

ALTER TABLE `statusy_odlotu`
  ADD PRIMARY KEY (`ID_Statusu`,`Status`);

ALTER TABLE `kraj-pasazer`
  ADD CONSTRAINT `Relacja10` FOREIGN KEY (`ID_Pasazera`) REFERENCES `pasazer` (`ID_Pasazera`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja9` FOREIGN KEY (`ID_Kraju`) REFERENCES `kraje` (`ID_Kraj`) ON UPDATE CASCADE ON DELETE RESTRICT;

ALTER TABLE `lot`
  ADD CONSTRAINT `Relacja1` FOREIGN KEY (`Miasto_Przylotu`) REFERENCES `lotniska` (`ID_Lotniska`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja2` FOREIGN KEY (`Miasto_Wylotu`) REFERENCES `lotniska` (`ID_Lotniska`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja3` FOREIGN KEY (`Linia_Lotnicza`) REFERENCES `linie_lotnicze` (`ID_Linia`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja8` FOREIGN KEY (`Pilot`) REFERENCES `pilot` (`ID_Pilota`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja4` FOREIGN KEY (`Status_Odlotu`) REFERENCES `statusy_odlotu` (`ID_Statusu`) ON UPDATE CASCADE ON DELETE RESTRICT;
ALTER TABLE `lot-pasazer`
  ADD CONSTRAINT `Relacja 7` FOREIGN KEY (`ID_Lotu`) REFERENCES `lot` (`ID_Lotu`) ON UPDATE CASCADE ON DELETE RESTRICT,
  ADD CONSTRAINT `Relacja6` FOREIGN KEY (`ID_Pasazera`) REFERENCES `pasazer` (`ID_Pasazera`) ON UPDATE CASCADE ON DELETE RESTRICT;

ALTER TABLE `lotniska`
  ADD CONSTRAINT `Relacja11` FOREIGN KEY (`kraj`) REFERENCES `kraje` (`ID_Kraj`) ON UPDATE CASCADE ON DELETE RESTRICT;

CREATE USER IF NOT EXISTS 'admin'@'localhost' IDENTIFIED BY 'maslo';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;

CREATE USER IF NOT EXISTS 'klient'@'localhost' IDENTIFIED BY '1234';
GRANT SELECT ON europejskie_linie_lotnicze.lot TO 'klient'@'localhost';

CREATE ROLE IF NOT EXISTS pracownik;
GRANT SELECT ON europejskie_linie_lotnicze.* TO pracownik;
GRANT SELECT, INSERT ON europejskie_linie_lotnicze.pasazer TO pracownik;

CREATE INDEX IF NOT EXISTS index1 ON pasazer(Imie, Nazwisko) USING HASH;
CREATE INDEX IF NOT EXISTS index2 ON pilot(Imie, Nazwisko);