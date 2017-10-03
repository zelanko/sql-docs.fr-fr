---
title: "Installer la recherche en texte intégral SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit comment installer la recherche en texte intégral de SQL Server sur Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 1f19074764820bddf2cc2a0e8fe4204120a5041d
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="install-sql-server-full-text-search-on-linux"></a>Installer la recherche en texte intégral SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Les étapes suivantes installer [recherche en texte intégral de SQL Server](https://msdn.microsoft.com/library/ms142571.aspx) (**FTP du serveur mssql**) sur Linux. Recherche en texte intégral vous permet d’exécuter des requêtes de texte intégral sur des données caractères dans des tables SQL Server. Pour les problèmes connus pour cette version, consultez le [Release Notes](sql-server-linux-release-notes.md).

> [!NOTE]
> Avant d’installer tout d’abord de recherche en texte intégral de SQL Server, [installer SQL Server](sql-server-linux-setup.md#platforms). Cela permet de configurer les clés et les référentiels que vous utilisez pour installer le **FTP du serveur mssql** package.

Installer la recherche en texte intégral de SQL Server pour votre plateforme :

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Installer sur RHEL</a>

Utilisez les commandes suivantes pour installer le **FTP du serveur mssql** sur Red Hat Enterprise Linux. 

```bash
sudo yum update
sudo yum install -y mssql-server-fts
```

Si vous avez déjà **FTP du serveur mssql** installé, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo yum check-update
sudo yum update mssql-server-fts
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package de recherche en texte intégral dans le [notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans la rubrique [installer SQL Server](sql-server-linux-setup.md#offline).

## <a name="ubuntu">Installer sur Ubuntu</a>

Utilisez les commandes suivantes pour installer le **FTP du serveur mssql** sur Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts
```

Si vous avez déjà **FTP du serveur mssql** installé, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts 
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package de recherche en texte intégral dans le [notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans la rubrique [installer SQL Server](sql-server-linux-setup.md#offline).

## <a name="SLES">Installez SLES</a>

Utilisez les commandes suivantes pour installer le **FTP du serveur mssql** sur SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-fts
```

Si vous avez déjà **FTP du serveur mssql** installé, vous pouvez mettre à jour vers la dernière version avec les commandes suivantes :

```bash
sudo zypper refresh
sudo zypper update mssql-server-fts
```

Si vous avez besoin d’une installation hors connexion, recherchez le téléchargement du package de recherche en texte intégral dans le [notes de publication](sql-server-linux-release-notes.md). Puis utilisez les mêmes étapes d’installation hors connexion décrites dans la rubrique [installer SQL Server](sql-server-linux-setup.md#offline).

## <a name="supported-languages"></a>Langues prises en charge

Recherche en texte intégral utilise [des analyseurs lexicaux](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) qui déterminent comment identifier les mots individuels en fonction de langue. Vous pouvez obtenir une liste des analyseurs lexicaux inscrits en interrogeant le **sys.fulltext_languages** affichage catalogue. Analyseurs lexicaux pour les langues suivantes sont installées avec SQL Server 2017 :

| Langage | ID de langue |
|---|---|
| Neutre | 0 |
| Arabe | 1025 |
| Bengali (Inde) | 1093 |
| Bokmål | 1044 |
| Brésilien | 1046 |
| British English | 2057 |
| Bulgare | 1026 |
| Catalan | 1027 |
| Chinois (Hong Kong R.A.S., RPC) | 3076 |
| Chinois (Macao R.A.S.) | 5124 |
| Chinois (Singapour) | 4100 |
| Croate | 1050 |
| Tchèque | 1029 |
| Danish | 1030 |
| Néerlandais | 1043 |
| Anglais | 1033 |
| Français | 1036 |
| Allemand | 1031 |
| Grec | 1032 |
| Goudjrati | 1095 |
| Hébreu | 1037 |
| Hindi | 1081 |
| Islandais | 1039 |
| Indonésien | 1057 |
| Italien | 1040 |
| Japonais | 1041 |
| Kannada | 1099 |
| Coréen | 1042 |
| Letton | 1062 |
| Lituanien | 1063 |
| Malais (Malaisie) | 1086 |
| Malayalam | 1100 |
| Marathe | 1102 |
| Polonais | 1045 |
| Portugais | 2070 |
| Pendjabi | 1094 |
| Roumain | 1048 |
| Russe | 1049 |
| Serbe (cyrillique) | 3098 |
| Serbe (latin) | 2074 |
| Chinois simplifié | 2052 |
| Slovaque | 1051 |
| Slovène | 1060 |
| Espagnol | 3082 |
| Suédois | 1053 |
| Tamoul | 1097 |
| Télougou | 1098 |
| Thaïlandais | 1054 |
| Chinois traditionnel | 1028 |
| Turc | 1055 |
| Ukrainien | 1058 |
| Ourdou | 1056 |
| Vietnamien | 1066 |

## <a id="filters"></a>Filtres

Recherche en texte intégral fonctionne également avec le texte stocké dans des fichiers binaires. Mais dans ce cas, un filtre installé est nécessaire pour traiter le fichier. Pour plus d’informations sur les filtres, consultez [configurer et gérer des filtres pour la recherche](../relational-databases/search/configure-and-manage-filters-for-search.md).

Vous pouvez afficher une liste des filtres installés en appelant **sp_help_fulltext_system_components 'filtre'**. Pour SQL Server 2017, les filtres suivants sont installés :

| Nom du composant | ID de classe | Version |
|---|---|---|
|.a | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ans | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ASC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ascx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asm | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ASP | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.aspx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asx | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bas | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bat | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.bcp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.c | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CLS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cmd | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CSA | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.CSS | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.csv | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DBS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.def | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dic | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DOS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.DSP | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ext | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.FAQ | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.fky | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.h | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hhc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hta | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.HTML | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htt | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htw | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hXX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.i | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ibq | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ICS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.idl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.idq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Inc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ini | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.INX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.jav | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Java | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.js | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.KCI | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.lgn | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.log | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.lst | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.m3u | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.MAK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.MK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.odc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.odh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.odl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgdef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgundef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pl | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.prc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.RC2 | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.reg | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rgs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.RTF | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rul | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.s | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SCC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.shtm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.shtml | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.snippet | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.sol | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SOR | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.srf | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.stm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.TAB | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tdl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tlh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tli | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.TRG | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.txt | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.UDF | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.UDT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.URL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.usr | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vbs | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.viw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.VSCT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixlangpack | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixmanifest | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vspscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vssscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wri | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wtx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.xml | 41B9BE05-B3AF-460C-BF0B-2CDD44A093B1 | 12.0.9735.0 |

## <a name="semantic-search"></a>Recherche sémantique
[La recherche sémantique](../relational-databases/search/semantic-search-sql-server.md) s’appuie sur la fonctionnalité de recherche en texte intégral pour extraire et d’index statistiquement pertinentes *expressions clés*. Cela vous permet d’interroger la signification des documents dans votre base de données. Il permet également d’identifier les documents sont similaires.

Pour pouvoir utiliser la recherche sémantique, vous devez d’abord restaurer la base de données de statistiques linguistiques de sémantique sur votre ordinateur.

1. Utiliser un outil, tel que [sqlcmd](sql-server-linux-setup-tools.md)pour exécuter la commande Transact-SQL suivante sur votre instance de SQL Server de Linux. Cette commande restaure la base de données de statistiques linguistiques.

   ```sql
   RESTORE DATABASE [semanticsdb] FROM
   DISK = N'/opt/mssql/misc/semanticsdb.bak' WITH FILE = 1,
   MOVE N'semanticsdb' TO N'/var/opt/mssql/data/semanticsDB.mdf',
   MOVE N'semanticsdb_log' TO N'/var/opt/mssql/data/semanticsdb_log.ldf', NOUNLOAD, STATS = 5
   GO
   ```

   > [!NOTE]
   > Si nécessaire, mettez à jour les chemins d’accès de la commande de restauration précédente pour s’adapter à votre configuration.

1. Exécutez la commande Transact-SQL suivante pour inscrire la base de données de statistiques linguistiques de sémantique.

    ```sql
    EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
    GO
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la recherche en texte intégral, consultez [recherche en texte intégral de SQL Server](../relational-databases/search/full-text-search.md). 

