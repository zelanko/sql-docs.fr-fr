---
title: Télécharger Microsoft JDBC Driver pour SQL Server
description: Télécharger le pilote Microsoft JDBC pour SQL Server pour développer des applications Java qui se connectent à SQL Server.
ms.date: 03/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f2e9f4d0c89438684201bef3bcb5d764af2cec1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922405"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Télécharger Microsoft JDBC Driver pour SQL Server

Le pilote Microsoft JDBC pour SQL Server est un pilote JDBC de type 4 offrant une connectivité de base de données par le biais des API JDBC standard, disponibles sur la plateforme Java. Les pilotes sont téléchargeables gratuitement pour tous les utilisateurs. Ils permettent d’accéder à SQL Server à partir d’une application Java, d’un serveur d’applications ou d’une applet Java.

## <a name="download"></a>Téléchargement

La version 8.2 est la dernière version en disponibilité générale. Elle prend en charge Java 8, 11 et 13. Si vous avez besoin de l’exécuter sur un runtime Java antérieur à celui-ci, consultez la matrice [Java et prise en charge de la spécification JDBC](microsoft-jdbc-driver-for-sql-server-support-matrix.md#java-and-jdbc-specification-support) pour voir s’il existe une version du pilote prise en charge que vous pouvez utiliser. Nous améliorons constamment la prise en charge de la connectivité Java. Nous vous recommandons donc vivement d’utiliser la dernière version de Microsoft JDBC Driver.

**[![Télécharger](../../ssms/media/download-icon.png) Télécharger le pilote Microsoft JDBC 8.2 pour SQL Server (zip)](https://go.microsoft.com/fwlink/?linkid=2122433)**  
**[![Télécharger](../../ssms/media/download-icon.png) Télécharger le pilote Microsoft JDBC 8.2 pour SQL Server (tar.gz)](https://go.microsoft.com/fwlink/?linkid=2122536)**  

### <a name="version-information"></a>Informations sur la version

- Numéro de version : 8.2.2
- Publication : 24 mars 2020

Lorsque vous téléchargez le pilote, il y a plusieurs fichiers JAR. Le nom du fichier JAR indique la version de Java qu’il prend en charge.

> [!Note]
> Si vous accédez à cette page à partir d’une version autre que l’anglais et que vous souhaitez voir le contenu le plus à jour, consultez la [version anglaise (États-Unis) du site](https://aka.ms/downloadmssqljdbcenglish). Vous pouvez télécharger différentes langues à partir du site en version anglaise (États-Unis) en sélectionnant [Langues disponibles](#available-languages).

## <a name="available-languages"></a>Langues disponibles

Cette version du pilote Microsoft JDBC pour SQL Server est disponible dans les langues suivantes :

Pilote Microsoft JDBC 8.2.2 pour SQL Server (zip) : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2122433&clcid=0x40a)

Pilote Microsoft JDBC 8.2.2 pour SQL Server (tar.gz) : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2122536&clcid=0x40a)

### <a name="release-notes"></a>Notes de publication

Pour plus d’informations sur cette version, consultez les [notes de publication](release-notes-for-the-jdbc-driver.md) et la [configuration requise](system-requirements-for-the-jdbc-driver.md).

### <a name="previous-releases"></a>Versions précédentes

Pour télécharger les versions précédentes, consultez [Versions précédentes du pilote Microsoft JDBC pour SQL Server](release-notes-for-the-jdbc-driver.md#previous-releases).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Utilisation du pilote JDBC avec Maven Central

Le pilote JDBC peut être ajouté à un projet Maven en tant que dépendance dans le fichier POM.xml avec le code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.2.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Pilotes non pris en charge

Les versions du pilote non prises en charge ne sont pas proposées en téléchargement ici. Nous améliorons constamment la prise en charge de la connectivité Java. Nous vous recommandons donc vivement d’utiliser la dernière version de Microsoft JDBC Driver.  
  
## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le pilote Microsoft JDBC pour SQL Server, consultez [Vue d’ensemble du pilote JDBC](overview-of-the-jdbc-driver.md) et le [référentiel GitHub du pilote JDBC](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
