local sStatus = closed

local file = io.open("status", "r")
sStatus = file:read()
file:close()

if sStatus == "closed" then
   redstone.setOutput("right", true)
   redstone.setOutput("left", false)
elseif sStatus == "open" then
   redstone.setOutput("right", false)
   redstone.setOutput("left", true)
else
   print "Please don't tamper with my code. :("
   sleep(3)
   os.reboot()
end

print "---------------------------------------------------"
print "Type 'Open' or 'Close' to Open or Close the airlock."
print "---------------------------------------------------"
while true do
local gen = math.random(1, 5)
print ""
write ">"
input = read()
if input == "open" then
   print "Starting Opening Sequence..."
   redstone.setOutput("right", false)
   redstone.setOutput("left", true)
   print(sStatus)
   sStatus = open
   print(sStatus)
   sleep(gen)
elseif input == "close" then
   print "Starting Closing Sequence..."
   redstone.setOutput("right", true)
   redstone.setOutput("left", false)
   print(sStatus)
   sStatus = closed
   print(sStatus)
   sleep(gen)
elseif input == "Open" then
   print "Staring Opening Sequence..."
   redstone.setOutput("right", false)
   redstone.setOutput("left", true)
   print(sStatus)
   sStatus = open
   print(sStatus)
   sleep(gen)
elseif input == "Close" then
   print "Starting Closing Sequence..."
   redstone.setOutput("right", true)
   redstone.setOutput("left", false)
   print(sStatus)	
   sStatus = closed
   print(sStatus)
   sleep(gen)
else
   print "Command not recognized." 
end
print "Sequence Completed..." 
sleep(3)
print(sStatus)
file = io.open("status", "w")
file:write(sStatus)
file:close()
--os.reboot()
end
