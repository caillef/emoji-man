![image](./.github/image.png)

## Emoji Man

1. Spawn 🪨 or 📄 or ✂️
2. Try and survive. RPS style mechanics.

### Resources:

- [dojobook](https://book.dojoengine.org/)
- [Cairo book](https://github.com/cairo-book/cairo-book.github.io/)
- [discord](https://discord.gg/dojoengine)
- [awesome dojo](https://github.com/dojoengine/awesome-dojo)

## Getting started in the Demo

### Prerequisites

Install Dojo:

```
curl -L https://install.dojoengine.org | bash
```

Then run the command:

```
dojoup
```

Running `dojoup` command will install the latest stable release of the Dojo (as of now [`v0.3.15`](https://github.com/dojoengine/dojo/releases/tag/v0.3.10)) tool suite.

### (Optional) Try out the starter first

`git clone https://github.com/dojoengine/dojo-starter`

### Step 1: Init main project

`git clone https://github.com/dojoengine/emoji-man`

a. Initialising the project  
b. Looking at the project structure  
c. Looking at the Scarb  
d. Cairo explanation

### Step 2: Your first model

a. Thinking about model structure  
b. Creating a model and their state structure. 101 on [ECS](https://github.com/SanderMertens/ecs-faq)  
c. Dojo is not purely ECS

### Step 3: Your first system

a. Creating a system - it's just a contract  
b. Adding a new system  
c. Run building via `sozo` to test

### Step 4: Adding a new model to a system

a. Adding a new model  
b. Adding a trait!!  
c. Using the trait in a system  
d. Running build to check

### Step 5: Sozo and the cli

a. Deeper into `sozo`  
b. Spinning up `katana`  
c. Spinning up `torii` and pointing to your World

Checkout out [`sozo`](https://book.dojoengine.org/toolchain/sozo/reference.html), [`katana`](https://book.dojoengine.org/toolchain/katana/reference.html), and [`torii`](https://book.dojoengine.org/toolchain/torii/reference.html) documentations.

### Step 6: Clean up

a. Clean up of code

### Step 7: Testing

a. Testing structure  
b. Writing a World deploy test  
c. Running the test

### Step 8: Deploying to Katana

a. Deploying and debugging

### Step 8: Client running

a. Running the client  
b. Generating models via npm  
c. Explaining the client structure - this is just one client, you can have many  
d. Explaining `torii` client

### Step 9: New model and syncing

a. Adding new model to contracts  
b. resyncing the client

### Step 10: Spinning up `slot` to deploy `katana` and `torii` instances remotely

a. What is [slot](https://github.com/cartridge-gg/slot)?

Run the following commands to install `slot`:

```
curl -L https://slot.cartridge.sh | bash
```

```bash
slotup
```

Log in to `slot`:

```bash
slot auth login

# Slot Auth debug (if old auth credentials):
rm ~/Library/Application\ Support/slot/credentials.json
```

b. Deployin

```bash
slot deployments create emoji-man-demo katana

# get credentials and save in Scarb.toml
slot deployments logs emoji-man-demo katana -f

# build a release
sozo --release build

# migrate release to katana
sozo --release migrate

# setup torri and point to the world
slot deployments create emoji-man-demo torii --rpc https://api.cartridge.gg/x/emoji-man-demo/katana --world 0x1fad58d91d5d121aa6dc4d16c01a161e0441ef75fe7d31e3664a61e66022b1f --start-block 1

# set auth (you will need to update the rpc_url to match your release)
./scripts/default_auth.sh release
```

d. Deploying a client to vercel - `use your own vercel account`

de. Multiplayer - share live link

## Next Steps

### Bonus 1: Optimistc Rendering

- Use RECS optimisc rendering to render the player in the client before the tx is confirmed

### Bonus 2: Show energy levels in the client

- Use RECS to show the energy levels in the client

### Bonus 3: Noise in map in Cairo and in Client

- Use [cubit](https://github.com/influenceth/cubit) simplex noise to restrict movement over mountains
- [noise](https://github.com/influenceth/sdk/blob/master/src/utils/simplex.js)

### Bonus 4: Add a collectables

- Add a way to spawn collectables on the map and allow players to collect them
