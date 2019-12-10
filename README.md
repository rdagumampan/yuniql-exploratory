# yuniqlx baseline

`yuniqlx baseline` is an experimental feature where we automate the script-generation of primary database objects and place results in `v0.00` of your migration project.  A command flow would look like this:

1. [Download latest `yuniqlx` build here](https://ci.appveyor.com/api/buildjobs/fqmphdr60lamkqvx/artifacts/yuniqlx-nightly.zip)
2. Setup your local workspace

	```bash
	yuniql init
	```

3. Baseline your db

	```bash
	yuniqlx baseline -c <your-source-database-connection-string> -p <your-v0.00-directory-path>
	```

4. Run your migration

	```bash
	yuniql run -c <your-source-database-connection-string> -a
	```

>NOTE: `yuniqlx` is an experimental feature and released as separate package. Because it's not everyday that we do baseline plus its heavy references to Sql Server SMO, I don't want to make this part of every release.

## Building the solution

Publish as self-contained application (win-x64)
```console
dotnet publish -c release -r win-x64 /p:publishsinglefile=true /p:publishtrimmed=true
```

Publish as optimized application (linux-x64)
```console
dotnet publish -c release -r linux-x64 /p:publishtrimmed=true
```

## References

https://docs.microsoft.com/en-us/sql/linux/tutorial-restore-backup-in-sql-server-container?view=sql-server-ver15
https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak
https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksLT2016.bak
https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak