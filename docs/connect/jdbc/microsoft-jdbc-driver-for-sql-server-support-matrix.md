---
title: Matrice de prise en charge de Microsoft JDBC Driver pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 950fa902d2772d131f5ecd626653ad58c97c0fb1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027893"
---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Matrice de support de Microsoft JDBC Driver pour SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Cette page contient la matrice de support et la politique de support de Microsoft JDBC Driver pour SQL Server.  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Matrice et politique de support de Microsoft JDBC Driver  
 La politique de support de Microsoft fournit des informations transparentes et prévisibles concernant la politique de support des produits Microsoft. Les versions 3.0, 4.x, 6.x et 7.x du pilote JDBC bénéficient de cinq ans de support standard à partir de la date de publication du pilote. Le support standard est défini sur le site web de la politique de support de Microsoft.  
  
 Les options de support étendu et personnalisé ne sont pas disponibles pour le pilote Microsoft JDBC.  
    
 Les pilotes Microsoft JDBC suivants bénéficient d’un support jusqu’à la date de fin de support indiquée.  
  
|Nom du pilote|Version de package du pilote|Fichier(s) JAR applicable(s)|Fin du support standard|
|-|-|-|-|  
|Microsoft JDBC Driver 7.4 pour SQL Server|7.4|mssql-jdbc-7.4.1.jre12.jar<br> mssql-jdbc-7.4.1.jre11.jar<br> mssql-jdbc-7.4.1.jre8.jar|2 août 2024|
|Microsoft JDBC Driver 7.2 pour SQL Server|7.2|mssql-jdbc-7.2.2.jre11.jar<br> mssql-jdbc-7.2.2.jre8.jar|16 avril 2024|
|Microsoft JDBC Driver 7.0 pour SQL Server|7.0|mssql-jdbc-7.0.0.jre10.jar<br> mssql-jdbc-7.0.0.jre8.jar|31 juillet 2023|  
|Microsoft JDBC Driver 6.4 pour SQL Server|6.4|mssql-jdbc-6.4.0.jre9.jar<br> mssql-jdbc-6.4.0.jre8.jar<br> mssql-jdbc-6.4.0.jre7.jar|27 février 2023|    
|Microsoft JDBC Driver 6.2 pour SQL Server|6.2|mssql-jdbc-6.2.2.jre8.jar<br> mssql-jdbc-6.2.2.jre7.jar|30 juin 2022|    
|Microsoft JDBC Driver 6.0 pour SQL Server|6.0|sqljdbc42.jar<br>sqljdbc41.jar|14 juillet 2021|    
|Microsoft JDBC Driver 4.2 pour SQL Server|4,2|sqljdbc42.jar<br>sqljdbc41.jar|24 août 2020|  
|Microsoft JDBC Driver 4.1 pour SQL Server|4,1|sqljdbc41.jar|12 décembre 2019|  
  
 Le support des pilotes Microsoft JDBC suivants est fini.  
 
|Nom du pilote|Version de package du pilote|Fin du support standard|  
|-|-|-|
|Microsoft JDBC Driver 4.0 pour SQL Server|4.0|6 mars 2017|  
|Pilote JDBC Microsoft SQL Server 3.0|3.0|23 avril 2015|  
|Microsoft SQL Server JDBC Driver 2.0|2|31 décembre 2012|  
|Pilote JDBC Microsoft SQL Server 2005 1.2|1.2|25 juin 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.1|1.1|25 juin 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.0|1.0|25 juin 2011|  
|Microsoft SQL Server 2000 JDBC Driver|2000|9 juillet 2010|  
  
## <a name="sql-version-compatibility"></a>Compatibilité des versions de SQL  
  
|Version du pilote|SQL Server 2008|SQL Server 2008 R2|SQL Server 2012|Azure SQL Database|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|SQL Server 2017|SQL Server 2019|  
|-|-|-|-|-|-|-|-|-|-|-|
|7.4|N|N|O|O|O|O|O|O|O|
|7.2|N|O|O|O|O|O|O|O|N| 
|7.0|N|O|O|O|O|O|O|O|N| 
|6.4|N|O|O|O|O|O|O|O|N| 
|6.2|O|O|O|O|O|O|O|O|N|
|6.1|O|O|O|O|O|O|O|N|N|
|6.0|O|O|O|O|O|O|O|N|N|
|4,2|O|O|O|O|O|O|O|N|N|
|4,1|O|O|O|O|O|O|O|N|N|
|4.0|O|O|O|O|O|O|O|N|N|
|3.0|O|O|A<sup>1</sup>|A<sup>2</sup>|N|A<sup>5</sup>|N|N|N|
|2|A<sup>3</sup>|A<sup>3</sup>|N|N|N|N|N|N|N|
|1.2|A<sup>3</sup>|N|N|N|N|N|N|N|N|
|1.1|N|N|N|N|N|N|N|N|N|  
|1.0|N|N|N|N|N|N|N|N|N|  
|2000|N|N|N|N|N|N|N|N|N|  
  
 <sup>1</sup>Microsoft SQL Server JDBC Driver version 3.0 peut se connecter à SQL Server 2012 comme client de bas niveau.  
  
 <sup>2</sup>La prise en charge d’Azure SQL Database a été introduite dans le pilote 3.0 sous la forme d’un correctif. Nous recommandons aux clients d’Azure SQL Database d’utiliser la dernière version disponible du pilote.  
  
 <sup>3</sup>Microsoft SQL Server JDBC Driver version 2.0 et Microsoft SQL Server 2005 JDBC Driver version 1.2 peuvent se connecter à SQL Server 2008 comme client de bas niveau. Quand des conversions de bas niveau sont autorisées, les applications peuvent exécuter des requêtes et effectuer des mises à jour sur les nouveaux types de données SQL Server 2008, comme date, time, datetime2, datetimeoffset et FILESTREAM. Pour plus d’informations sur l’utilisation de ces nouveaux types de données avec le pilote JDBC, consultez  [Working with SQL Server 2008 Date/Time Data Types using JDBC Driver](https://go.microsoft.com/fwlink/?LinkId=145198) et  [Working with SQL Server 2008 FileStream using JDBC Driver](https://go.microsoft.com/fwlink/?LinkId=145199). Pour plus d’informations sur la compatibilité de bas niveau de ces nouveaux types de données, consultez les rubriques  [Utilisation des données de date et d’heure](https://go.microsoft.com/fwlink/?LinkId=145211)et  [FILESTREAM Support](https://go.microsoft.com/fwlink/?LinkId=145212) dans la documentation en ligne de SQL Server.  
  
 <sup>4</sup>La prise en charge des connexions entre le pilote Microsoft JDBC Driver et Parallel Data Warehouse a été introduite dans Microsoft JDBC Driver 4.0 pour SQL Server et Microsoft SQL Server 2008 R2 Parallel Data Warehouse Appliance Update 3.  
  
 <sup>5</sup>Microsoft SQL Server JDBC Driver version 3.0 peut se connecter à SQL Server 2014 comme client de bas niveau.  
  
## <a name="java-and-jdbc-specification-support"></a>Java et prise en charge de la spécification JDBC  
  
|Version du pilote JDBC|Versions de JRE|Version de l’API JDBC| 
|-|-|-|  
|7.4|1.8, 11, 12|4.2, 4.3 (partiellement)|
|7.2|1.8, 11|4.2, 4.3 (partiellement)|
|7.0|1.8, 10|4.2, 4.3 (partiellement)|
|6.4|1.7, 1.8, 9|4.1, 4.2, 4.3 (partiellement)|  
|6.2|1.7, 1.8|4.1, 4.2|  
|6.1|1.7, 1.8|4.1, 4.2|  
|6.0|1.7, 1.8|4.1, 4.2|  
|4,2|1.7, 1.8|4.1, 4.2|  
|4,1|1.7|4.0|  
|4.0|1.5, 1.6, 1.7|3.0, 4.0|  
|3.0|1.5, 1.6,|3.0, 4.0|  
|2|1.5, 1.6|3.0, 4.0|  
|1.2|1.4, 1.5, 1.6|3.0|  
|1.1|1.4|3.0|  
|1.0|1.4|3.0|  
|2000|1.4|3.0|  
  
## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge  
 Le pilote Microsoft JDBC est conçu pour fonctionner sur tout système d’exploitation prenant en charge l’utilisation d’une machine virtuelle Java (JVM). Les plateformes couramment utilisées sont notamment Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Server 2008 R2, Windows Vista, Linux, Unix, AIX et MacOS.  
  
 L’équipe du produit JDBC teste notre pilote sur Windows, Sun Solaris, SUSE Linux et RedHat Linux.  Le support technique est disponible pour les clients sur toutes les plateformes, mais nous sommes susceptibles de vous demander de reproduire le problème sur une plateforme comme Windows.  
  
## <a name="application-server-support"></a>Prise en charge des serveurs d’applications  
 Le pilote Microsoft JDBC pour SQL Server est testé avec différents serveurs d’applications.  Pour plus d’informations sur la version du pilote compatible avec leur produit, consultez le fournisseur de votre serveur d’applications.
 
 
