# Starting Local MongoDB

## Option 1: Start MongoDB Service (Windows)

```powershell
# Start MongoDB as a Windows Service
net start MongoDB
```

## Option 2: Start MongoDB Manually

If MongoDB is not in your PATH, navigate to your MongoDB installation directory:

```powershell
# Common installation path
cd "C:\Program Files\MongoDB\Server\{version}\bin"

# Start MongoDB server
.\mongod.exe --dbpath "C:\data\db"
```

**Note**: Make sure the data directory exists:
```powershell
# Create data directory if it doesn't exist
New-Item -ItemType Directory -Force -Path C:\data\db
```

## Option 3: Find MongoDB Installation

```powershell
# Search for MongoDB installation
Get-ChildItem -Path "C:\Program Files\MongoDB" -Recurse -Filter mongod.exe -ErrorAction SilentlyContinue
```

## Verify MongoDB is Running

```powershell
# Check if MongoDB is listening on port 27017
Test-NetConnection -ComputerName localhost -Port 27017
```

## After MongoDB is Running

1. Your `.env` file is already updated to use local MongoDB:
   ```
   MONGODB_URI=mongodb://localhost:27017/taskmanager
   ```

2. Start your healthcare app:
   ```powershell
   node server-mongodb.js
   ```

3. Your data will now be stored locally in MongoDB instead of the cloud!

## Troubleshooting

### MongoDB Service Won't Start
- Check if MongoDB is installed correctly
- Verify the data directory exists
- Check Windows Services (services.msc) for MongoDB status

### Cannot Find MongoDB
Try these common locations:
- `C:\Program Files\MongoDB\Server\`
- `C:\Program Files\MongoDB Community\Server\`
- Check your Downloads folder for MongoDB installer

### Still Having Issues?
You can continue using MongoDB Atlas (cloud) by reverting `.env`:
```bash
MONGODB_URI=mongodb+srv://soujanyapoojari64_db_user:xjtYSHgChOJHIhFn@cluster0.iexsixj.mongodb.net/taskmanager
```
