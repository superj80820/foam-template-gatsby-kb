Consider two ways of doing the same thing:

```java
PreparedStatement stmt = conn.createStatement("INSERT INTO students VALUES('" + user + "')");
stmt.execute();
```

Or

```java
PreparedStatement stmt = conn.prepareStatement("INSERT INTO student VALUES(?)");
stmt.setString(1, user);
stmt.execute();
```

If "user" came from user input and the user input was

```haskell
Robert'); DROP TABLE students; --
```

Then in the first instance, you'd be hosed. In the second, you'd be safe and Little Bobby Tables would be registered for your school.

Ref: https://stackoverflow.com/questions/1582161/how-does-a-preparedstatement-avoid-or-prevent-sql-injection