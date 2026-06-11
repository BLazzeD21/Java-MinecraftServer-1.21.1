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

# Automatic Server Restart (systemd)

To ensure the Minecraft Forge server automatically starts after a system reboot and restarts after crashes, use a systemd service.

## Find the Server Directory

Locate the generated Forge startup script:

```bash
find / -name run.sh 2>/dev/null
```

Example output:

```text
/home/server/run.sh
```

## Create the systemd Service

Create a new service file:

```bash
sudo nano /etc/systemd/system/minecraft.service
```

Add the following configuration:

```ini
[Unit]
Description=Minecraft Forge Server
After=network.target

[Service]
Type=simple
WorkingDirectory=/home/server
ExecStart=/bin/bash /home/server/run.sh

# Automatically restart the server if it crashes
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

> Replace `/home/server` with the actual path to your Minecraft server directory.

## Enable and Start the Service

Reload systemd:

```bash
sudo systemctl daemon-reload
```

Enable automatic startup on boot:

```bash
sudo systemctl enable minecraft
```

Start the server:

```bash
sudo systemctl start minecraft
```

Check service status:

```bash
sudo systemctl status minecraft
```

## Useful Commands

Restart the server:

```bash
sudo systemctl restart minecraft
```

Stop the server:

```bash
sudo systemctl stop minecraft
```

View live logs:

```bash
tail -f /home/server/logs/latest.log
```

View systemd logs:

```bash
journalctl -u minecraft -f
```

---

# Installing mcrcon

RCON allows remote administration of the Minecraft server.

## Install Build Dependencies

```bash
apt update
apt install gcc make git -y
```

## Download and Build mcrcon

```bash
cd /tmp
git clone https://github.com/Tiiffi/mcrcon.git
cd mcrcon

make
cp mcrcon /usr/local/bin/
chmod +x /usr/local/bin/mcrcon
```

Verify installation:

```bash
mcrcon -h
```

---

## Connecting via RCON

Make sure RCON is enabled in `server.properties`:

```properties
enable-rcon=true
rcon.port=25575
rcon.password=your_password
```

Restart the server after changing these settings:

```bash
sudo systemctl restart minecraft
```

## Local Connection

Connect from the server itself:

```bash
mcrcon -H 127.0.0.1 -P 25575 -p your_password
```

## Execute a Single Command

List online players:

```bash
mcrcon -H 127.0.0.1 -P 25575 -p your_password list
```

Broadcast a message:

```bash
mcrcon -H 127.0.0.1 -P 25575 -p your_password "say Server restart in 5 minutes"
```

Stop the server:

```bash
mcrcon -H 127.0.0.1 -P 25575 -p your_password stop
```

---

# Troubleshooting

Check if the RCON port is listening:

```bash
ss -tulpn | grep 25575
```

Expected output:

```text
LISTEN 0 50 0.0.0.0:25575
```

If the port is not open:

1. Verify `enable-rcon=true`
2. Verify the RCON password is configured
3. Restart the server
4. Check the logs:

```bash
tail -f /home/server/logs/latest.log
```

Successful startup should contain:

```text
Done (xx.xxxs)! For help, type "help"
Starting remote control listener
RCON running on 0.0.0.0:25575
```


## Mods

**Structures and Travel**
- Blue Skies (новые измерения, уникальные боссы, данжи и собственная система прогрессии)
- Twilight Forest (измерение с боссами, лабиринтами и последовательным прохождением)
- YUNG's Better Dungeons (полностью переработанные подземелья с улучшенным лутом)
- YUNG's Better Strongholds (масштабно обновлённые крепости Энда)
- YUNG's Better Mineshafts (улучшенные шахты с новой генерацией и структурами)
- When Dungeons Arise (огромные замки, крепости и руины по всему миру)
- Towns and Towers (новые варианты деревень, башен и поселений)

**Construction**
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

**Transport and technology**
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

**Mobs**
- Alex's Mobs (80+ новых животных и существ с уникальными механиками)
- Naturalist (реалистичные животные для более живого мира)

**Optimization**
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

**Other**
- Sophisticated Backpacks (рюкзаки с улучшениями, фильтрами и автоматизацией)
- Iron Chests (сундуки увеличенного объёма разных уровней)
- JEI (Just Enough Items) (просмотр рецептов и информации о предметах)
- Jade (информация о блоках и мобах под прицелом)
- Xaero's Minimap (мини-карта с метками и навигацией)
- Dynamic Lights (динамическое освещение от предметов в руках)
- ItemPhysic (реалистичная физика выпавших предметов)

## Notes

* Forge 47.4.20 requires Java 17.
* All mods must be compatible with Minecraft 1.20.1 and Forge 47.x.
* If the server fails to start, verify the Java version and check mod compatibility.

