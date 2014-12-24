---
layout: black_white
title: Lua代码片段收集
---

```lua
--[[@Func :闭包
    @Desc : 当一个函数内部嵌套另一个函数定义时，内部的函数体可以访问外部的函数的局部变量，这种特征我们称作词法定界]]
function fuck()
    local i = 0
    return function()
        i = i + 1
        return i
    end
end

c1 = fuck()
print(c1())
print(c1())
```


```lua
-- Desc : 序列化Lua表(Convert Lua-Table To String)
function serialize(t)
	local mark={}
	local assign={}
	
	local function ser_table(tbl,parent)
		mark[tbl]=parent
		local tmp={}
		for k,v in pairs(tbl) do
			local key= type(k)=="number" and "["..k.."]" or k
			if type(v)=="table" then
				local dotkey= parent..(type(k)=="number" and key or "."..key)
				if mark[v] then
					table.insert(assign,dotkey.."="..mark[v])
				else
					table.insert(tmp, key.."="..ser_table(v,dotkey))
				end
			else
				table.insert(tmp, key.."="..v)
			end
		end
		return "{"..table.concat(tmp,",").."}"
	end
 
	return "do local ret="..ser_table(t,"ret")..table.concat(assign," ").." return ret end"
end
```

```lua
-- 实现Java字符串的Hash算法
hash = function(input)
    input = tostring(input);
    local h = 0
    local len = string.len(input)
    local max = 2147483647
    local min = -2147483648
    local cycle = 4294967296
 
    for i=1, len do
        h = 31 * h + string.byte(string.sub(input, i, i));
        while h > max do
            h = h - cycle
        end
        while h < min do
            h = h + cycle
        end
    end
    return h
end
```

```lua
--Desc : coroutine实现异步通信-取代callback
function runAsyncFunc( func, ... )
    local current = coroutine.running
    func(function (  )
        coroutine.resume(current)
    end, ...)
    coroutine.yield()
end

-- test it as follows:[实现A-B-C严格依次Call]
jeffValue = "O"
function funcA()
	jeffValue = "A"
	print(jeffValue)
end

function funcB()
	local n , s , s0 = 0 

	-- delay 3 second execute
	local start = os.time()
	print("start second is " .. os.date("%S" , os.time()))
	while true do
	    s = os.date("%S" , os.time());
	    now = os.time()
	    if now - start >= 3 then
	    	jeffValue = "B"
			print(jeffValue)
			print("now second is " .. os.date("%S" , os.time()))
	        break;
	    end;
	end;
end

function funcC()
	jeffValue = "C"
	print(jeffValue)
end

co = coroutine.create(function (  )
    funcA()
    funcB()
    funcC()
end)

coroutine.resume(co)
coroutine.resume(co)
coroutine.resume(co)

-- execute test code输出如下:
A  
start second is 55  
B  
now second is 58   
C   
```