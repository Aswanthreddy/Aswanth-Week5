# Aswanth-Week5
# Step 1: Install dependencies
sudo apt update
sudo apt install -y build-essential cmake swig python3 python3-pip python3-venv \
git clang bison flex libreadline-dev gawk tcl-dev libffi-dev graphviz xdot \
pkg-config libboost-system-dev libboost-python-dev libboost-filesystem-dev \
zlib1g-dev

# Step 2: Clone OpenROAD Flow Scripts
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
cd OpenROAD-flow-scripts

# Step 3: Run setup script
./setup.sh

# Step 4: Export environment
export OPENROAD_HOME=$(pwd)
export PATH=$OPENROAD_HOME/tools/OpenROAD/bin:$PATH
cd OpenROAD-flow-scripts/flow

# Run only floorplan and placement stages
make DESIGN_CONFIG=./designs/sky130hd/aes/config.mk floorplan
make DESIGN_CONFIG=./designs/sky130hd/aes/config.mk place
| Stage     | File/Directory                         | Description                      |
| --------- | -------------------------------------- | -------------------------------- |
| Floorplan | `results/aes/floorplan.def`            | Defines core and die area        |
| Placement | `results/aes/place.def`                | Contains placed standard cells   |
| Logs      | `logs/floorplan.log`, `logs/place.log` | Execution reports for each stage |
| Step              | Task                      | Status       |
| ----------------- | ------------------------- | ------------ |
| Environment Setup | OpenROAD installation     | ✅ Completed  |
| Floorplan Stage   | Core + Die area generated | ✅ Completed  |
| Placement Stage   | Standard cells placed     | ✅ Completed  |
| Verification      | Layout and log check      | ✅ Successful |
| Challenge                      | Solution                                            |
| ------------------------------ | --------------------------------------------------- |
| Dependency errors during setup | Installed missing `libboost` and `tcl-dev` packages |
| PATH not recognized            | Exported OpenROAD binary path manually              |
| Long compile time              | Used system with 8GB RAM + swap space enabled       |
