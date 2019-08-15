# Saving-with-NSCoding

extension FileManager
```
public extension FileManager {
  static var documentDirectoryURL: URL {
    return `default`.urls(for: .documentDirectory, in: .userDomainMask)[0]
  }
}
```

Strings
=======
```
let myString = "Lorem ipsum dolor sit amet"
let pathURL = FileManager.documentDirectoryURL.appendingPathComponent("myString").appendingPathExtension("swift")
let data = try NSKeyedArchiver.archivedData(withRootObject: myString, requiringSecureCoding: false)

// Write
do {
  try data.write(to: pathURL)
} catch {
  print("Couldn't write file")
}

// Read
do {
  if let loadedString = try NSKeyedUnarchiver.unarchiveTopLevelObjectWithData(data) as? String {
      print(loadedString)
  }
} catch {
  print("Couldn't read file.")
}
```

Arrays
======
```
let myArray = ["item0", "item1", "item2"]
let pathURL = FileManager.documentDirectoryURL.appendingPathComponent("array001").appendingPathExtension("swift")
let data = try NSKeyedArchiver.archivedData(withRootObject: myArray, requiringSecureCoding: false)

// Write
do {
  try data.write(to: pathURL)
} catch {
  print("Couldn't write file")
}

// Read
do {
  if let loadedMyArray = try NSKeyedUnarchiver.unarchiveTopLevelObjectWithData(data) as? [String] {
    for item in loadedMyArray {
      print(item)
    }
  }
} catch {
  print("Couldn't read file.")
}
```

Dictionaries
============
```
let myDictionary = ["key0": "Alpha", "key1": "Bravo", "key2": "Charlie"]
let pathURL = FileManager.documentDirectoryURL.appendingPathComponent("array001").appendingPathExtension("swift")
let data = try NSKeyedArchiver.archivedData(withRootObject: myDictionary, requiringSecureCoding: false)

// Write
do {
  try data.write(to: pathURL)
} catch {
  print("Couldn't write file")
}

// Read
do {
  if let loadedMyDictionary = try NSKeyedUnarchiver.unarchiveTopLevelObjectWithData(data) as? [String: String] {
    for (key, value) in loadedMyDictionary {
      print("\(key) -> \(value)")
    }
  }
} catch {
  print("Couldn't read file.")
}
```







