---
title: Télécharger Microsoft JDBC Driver pour SQL Server
description: Télécharger le pilote Microsoft JDBC pour SQL Server pour développer des applications Java qui se connectent à SQL Server.
ms.date: 02/26/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6576ed155e57fbd69757065c440382efa4adba5e
ms.sourcegitcommit: 6ee40a2411a635daeec83fa473d8a19e5ae64662
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77903496"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Télécharger Microsoft JDBC Driver pour SQL Server

Cet article contient des liens permettant de télécharger le pilote Microsoft JDBC pour SQL Server. Ce pilote vous permet de développer des applications Java qui se connectent à SQL Server.  

## <a name="available-downloads-of-jdbc-driver-for-sql-server"></a>Téléchargements disponibles du pilote JDBC pour SQL Server

Utilisez les liens figurant dans le tableau suivant pour télécharger la dernière version du pilote Microsoft JDBC pour SQL Server qui correspond à votre Java Runtime Environment (JRE) :

| Version | Date de publication | Versions Java |
|---|---|---|
| [Microsoft JDBC Driver 8.2](https://go.microsoft.com/fwlink/?linkid=2116870) | 26/2/2020 | JRE 8, 11, 13 |
| [Microsoft JDBC Driver 7.4](https://go.microsoft.com/fwlink/?linkid=2099962) | 1/8/2019 | JRE 8, 11, 12 |
| [Microsoft JDBC Driver 7.2](https://go.microsoft.com/fwlink/?linkid=2063159) | 17/4/2019 | JRE 8, 11 |
| [Microsoft JDBC Driver 7.0](https://go.microsoft.com/fwlink/?linkid=2005972) | 31/7/2018 | JRE 8, 10 |
| [Microsoft JDBC Driver 6.4](https://go.microsoft.com/fwlink/?linkid=868290)  | 26/3/2018 | JRE 7, 8, 9 |
| [Microsoft JDBC Driver 6.2](https://go.microsoft.com/fwlink/?linkid=852460) | 12/2/2018 | JRE 7, 8 |
| [Microsoft JDBC Driver 6.0](https://go.microsoft.com/fwlink/?LinkId=245496) | 27/2/2018 | JRE 7, 8 |
| [Microsoft JDBC Driver 4.2](https://go.microsoft.com/fwlink/?linkid=841534) | 26/2/2018 | JRE 7, 8 |

Lorsque vous téléchargez le pilote, il y a plusieurs fichiers JAR. Le nom du fichier JAR indique la version de Java qu’il prend en charge. Pour plus d’informations sur chaque version, reportez-vous aux [notes de publication](release-notes-for-the-jdbc-driver.md) et à la [configuration système requise](system-requirements-for-the-jdbc-driver.md).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Utilisation du pilote JDBC avec Maven Central

Le pilote JDBC peut être ajouté à un projet Maven en tant que dépendance dans le fichier POM.xml avec le code suivant :

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.2.1.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Pilotes non pris en charge

Les versions du pilote non prises en charge ne sont pas proposées en téléchargement ici. Nous améliorons constamment la prise en charge de la connectivité Java. Nous vous recommandons donc vivement d’utiliser la dernière version de Microsoft JDBC Driver.  
  
## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le pilote Microsoft JDBC pour SQL Server, consultez [Vue d’ensemble du pilote JDBC](overview-of-the-jdbc-driver.md) et le [référentiel GitHub du pilote JDBC](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
