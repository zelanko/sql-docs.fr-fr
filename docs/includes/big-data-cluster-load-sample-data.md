### <a id="sampledata"></a> Charger des exemples de données

Didacticiels de cluster de données volumineuses de SQL Server utilisent un ensemble commun d’exemples de données. Pour configurer les exemples de données sur votre cluster de données volumineux, utilisez les étapes suivantes :

1. Si vous n’avez pas d’outils de ligne de commande SQL Server (**sqlcmd** et **bcp**) installé, installez tout d’abord ces outils avec un des liens :

   * **Windows**: [outils de ligne de commande d’installer SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=53591)
   * **Linux**: [outils de ligne de commande d’installer SQL Server sur Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-tools)

1. Télécharger l’exemple de fichier de sauvegarde [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) sur votre ordinateur.

1. Accédez au cluster SQL Server 2019 big data [répertoire d’exemples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster).

1. Téléchargez le [bootstrap-exemples-db.sql](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql) script Transact-SQL.

1. Téléchargez et exécutez une des deux exemples de scripts suivants à partir de la ligne de commande :

   * **Windows**: [bootstrap-exemples-db.cmd](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd)
   * **Linux**: [bootstrap-exemples-db.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh)

   > [!TIP]
   > Vous pouvez obtenir des instructions d’utilisation en exécutant le script sans paramètre.

Le script restaure la base de données à l’instance principale de SQL Server et charge également des données dans HDFS dans le pool de stockage.