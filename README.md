# Minecraft Forge 1.20.1 Server Setup (Ubuntu)

## Requirements

* Ubuntu Server or Ubuntu Desktop
* Java 17
* `forge-1.20.1-47.4.20-installer.jar`

## Install Java

Update package lists and install Java 17:

```bash
sudo apt update
sudo apt install -y openjdk-17-jre-headless
```

Verify the installation:

```bash
java -version
```

The output should show Java 17.

## Create the Server Directory

Create a directory for the server and move into it:

```bash
mkdir -p ~/minecraft-server
cd ~/minecraft-server
```

Place `forge-1.20.1-47.4.20-installer.jar` in this directory.

## Install the Forge Server

Run the installer:

```bash
java -jar forge-1.20.1-47.4.20-installer.jar --installServer
```

This will download and install all required server files.

## Accept the Minecraft EULA

Open the EULA file:

```bash
nano eula.txt
```

Change:

```text
eula=false
```

to:

```text
eula=true
```

Save and close the file.

## First Server Start

Start the server:

```bash
bash run.sh
```

After the server finishes loading, stop it using:

```text
stop
```

## Installing Mods

Copy all server-side mods into the following directory:

```text
mods/
```

If your modpack includes additional configuration files, copy:

```text
config/
defaultconfigs/
```

into the server directory as well.

## Starting the Server

Launch the server:

```bash
bash run.sh
```

## Useful Commands

Check memory usage:

```bash
free -h
```

View running Java processes:

```bash
ps aux | grep java
```

Stop the server from the console:

```text
stop
```

## Server Directory Structure

```text
minecraft-server/
├── mods/
├── config/
├── defaultconfigs/
├── world/
├── eula.txt
├── server.properties
├── run.sh
└── libraries/
```

## Mods

**Структуры и исследование**
- Blue Skies (новые измерения, уникальные боссы, данжи и собственная система прогрессии)
- Twilight Forest (измерение с боссами, лабиринтами и последовательным прохождением)
- YUNG's Better Dungeons (полностью переработанные подземелья с улучшенным лутом)
- YUNG's Better Strongholds (масштабно обновлённые крепости Энда)
- YUNG's Better Mineshafts (улучшенные шахты с новой генерацией и структурами)
- When Dungeons Arise (огромные замки, крепости и руины по всему миру)
- Towns and Towers (новые варианты деревень, башен и поселений)

**Строительство**
- MrCrayfish's Furniture: Refurbished (мебель, бытовая техника и декор для дома)
- Macaw's Bridges (декоративные мосты разных стилей и материалов)
- Macaw's Doors (большой выбор новых дверей)
- Macaw's Roofs (блоки и элементы для красивых крыш)
- Supplementaries (декор и полезные механики для повседневной игры)
- Handcrafted (множество мебели и украшений для интерьеров)
- Chipped (сотни декоративных вариантов стандартных блоков)
- Rechiseled (новые текстурные варианты и стили оформления блоков)
- Another Furniture (дополнительные наборы мебели для строительства)
- Decorative Blocks (колонны, балки, решётки и декоративные элементы)
- Amendments (улучшения и дополнения для декоративных модов)
- Транспорт и технологии
- Create (механизмы, автоматизация, производство и транспортные системы)
- Create: Steam 'n' Rails (расширенные железные дороги, локомотивы и вагоны)
- Create Crafts & Additions (электричество, моторы, аккумуляторы и новые механизмы)
- Create Deco (декоративные блоки в индустриальном стиле Create)
- Valkyrien Skies (физика движущихся кораблей и построек)
- Eureka! Airships! (создание и управление воздушными кораблями)
- Clockwork (самолёты, двигатели и механическая техника на базе Create и Valkyrien Skies)

**Зверье**
- Alex's Mobs (80+ новых животных и существ с уникальными механиками)
- Naturalist (реалистичные животные для более живого мира)

**Полезное**
- Sophisticated Backpacks (рюкзаки с улучшениями, фильтрами и автоматизацией)
- Iron Chests (сундуки увеличенного объёма разных уровней)
- JEI (Just Enough Items) (просмотр рецептов и информации о предметах)
- Jade (информация о блоках и мобах под прицелом)
- Xaero's Minimap (мини-карта с метками и навигацией)
- Dynamic Lights (динамическое освещение от предметов в руках)
- ItemPhysic (реалистичная физика выпавших предметов)

**Структуры и исследование**
- Blue Skies (новые измерения, уникальные боссы, данжи и собственная система прогрессии)
- Twilight Forest (измерение с боссами, лабиринтами и последовательным прохождением)
- YUNG's Better Dungeons (полностью переработанные подземелья с улучшенным лутом)
- YUNG's Better Strongholds (масштабно обновлённые крепости Энда)
- YUNG's Better Mineshafts (улучшенные шахты с новой генерацией и структурами)
- When Dungeons Arise (огромные замки, крепости и руины по всему миру)
- Towns and Towers (новые варианты деревень, башен и поселений)

**Строительство**
- MrCrayfish's Furniture: Refurbished (мебель, бытовая техника и декор для дома)
- Macaw's Bridges (декоративные мосты разных стилей и материалов)
- Macaw's Doors (большой выбор новых дверей)
- Macaw's Roofs (блоки и элементы для красивых крыш)
- Supplementaries (декор и полезные механики для повседневной игры)
- Handcrafted (множество мебели и украшений для интерьеров)
- Chipped (сотни декоративных вариантов стандартных блоков)
- Rechiseled (новые текстурные варианты и стили оформления блоков)
- Another Furniture (дополнительные наборы мебели для строительства)
- Decorative Blocks (колонны, балки, решётки и декоративные элементы)
- Amendments (улучшения и дополнения для декоративных модов)

**Транспорт и технологии**
- Create (механизмы, автоматизация, производство и транспортные системы)
- Create: Steam 'n' Rails (расширенные железные дороги, локомотивы и вагоны)
- Create Crafts & Additions (электричество, моторы, аккумуляторы и новые механизмы)
- Create Deco (декоративные блоки в индустриальном стиле Create)
- Create: Copycats+ (расширенные копикат-блоки для создания сложных декоративных конструкций и маскировки механизмов)
- Create: Connected (соединённые текстуры и улучшенное визуальное оформление блоков Create)
- Create: New Age (электроэнергия, генераторы, катушки Теслы, современные технологии и интеграция с Create)
- Valkyrien Skies (физика движущихся кораблей и построек)
- Eureka! Airships! (создание и управление воздушными кораблями)
- Clockwork (самолёты, двигатели и механическая техника на базе Create и Valkyrien Skies)

**Зверье**- 
- Alex's Mobs (80+ новых животных и существ с уникальными механиками)
- Naturalist (реалистичные животные для более живого мира)

**Полезное**
- Sophisticated Backpacks (рюкзаки с улучшениями, фильтрами и автоматизацией)
- Iron Chests (сундуки увеличенного объёма разных уровней)
- JEI (Just Enough Items) (просмотр рецептов и информации о предметах)
- Jade (информация о блоках и мобах под прицелом)
- Xaero's Minimap (мини-карта с метками и навигацией)
- Dynamic Lights (динамическое освещение от предметов в руках)
- ItemPhysic (реалистичная физика выпавших предметов)

**Оптимизация**
- Entity Culling (повышение FPS за счёт скрытия невидимых сущностей)
- FerriteCore (снижение потребления оперативной памяти)
- Embeddium (значительный прирост FPS и графическая оптимизация)
- ModernFix (комплексное улучшение производительности и загрузки игры)
- Chunky (предварительная генерация чанков для уменьшения лагов)
- Entity Culling (повышение FPS за счёт скрытия невидимых сущностей)
- FerriteCore (снижение потребления оперативной памяти)
- Embeddium (значительный прирост FPS и графическая оптимизация)
- ModernFix (комплексное улучшение производительности и загрузки игры)
- Chunky (предварительная генерация чанков для уменьшения лагов)
- AI Improvements (оптимизация ИИ мобов и снижение нагрузки на сервер)
- FastSuite (ускорение серверных операций и улучшение производительности)
- FastWorkbench (оптимизация системы крафта и снижение нагрузки от верстаков)
- FastFurnace (оптимизация работы печей и плавильных процессов)

## Notes

* Forge 47.4.20 requires Java 17.
* All mods must be compatible with Minecraft 1.20.1 and Forge 47.x.
* If the server fails to start, verify the Java version and check mod compatibility.

This version is suitable for GitHub, GitLab, or a private project repository.

