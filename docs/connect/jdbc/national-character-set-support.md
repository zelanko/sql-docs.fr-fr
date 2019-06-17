---
title: Prise en charge du jeu de caractères nationaux | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ab17d9e60752b1aea747b03947d235b7d5f91605
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801804"
---
# <a name="national-character-set-support"></a>Prise en charge du jeu de caractères nationaux
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le pilote JDBC prend en charge l'API JDBC 4.0, qui comprend désormais de nouvelles méthodes d'API de conversion de jeu de caractères nationaux. Cette prise en charge inclut de nouvelles méthodes setter, getter et updater pour **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, et **NCLOB** types JDBC.  
  
 La liste suivante répertorie les nouvelles méthodes getter, setter et updater de prise en charge de la conversion du jeu de caractères nationaux :  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) : [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) : [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) : [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Vous devez définir l'instruction classpath de façon à inclure le fichier sqljdbc4.jar pour utiliser ces méthodes dans votre application.  
  
 Pour envoyer des paramètres String au serveur au format Unicode, les applications doivent soit utiliser les nouvelles méthodes JDBC 4.0 prenant en charge les caractères nationaux, soit affecter la valeur « **true** » à la propriété de connexion **sendStringParametersAsUnicode** lorsqu’elles utilisent les méthodes basées sur des caractères non nationaux. Il est recommandé d'utiliser les nouvelles méthodes JDBC 4.0 prenant en charge les caractères nationaux chaque fois que cela est possible. Pour plus d’informations sur la **sendStringParametersAsUnicode** propriété de connexion, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
