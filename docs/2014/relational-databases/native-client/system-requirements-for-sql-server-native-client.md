---
title: Configuration système requise pour SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- system requirements [SQL Server Native Client]
- data access [SQL Server Native Client], system requirements
- SQL Server Native Client, system requirements
- SQLNCLI, system requirements
ms.assetid: 1c8e2f8a-a440-44da-8e3a-af632d34c52c
caps.latest.revision: 60
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbabe38f62a9bd581bd9e41ab508336332bc3983
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417948"
---
# <a name="system-requirements-for-sql-server-native-client"></a>Configuration requise pour SQL Server Native Client
  Pour utiliser les fonctionnalités d'accès aux données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple MARS, les logiciels suivants doivent être installés :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sur votre client.  
  
-   Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur votre serveur.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client requiert Windows Installer 3.0. Windows Installer 3.0 est déjà installé sur les systèmes d'exploitation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Pour toutes les autres plateformes, vous devez l'installer explicitement. Pour plus d’informations, consultez [Windows Installer 3.0 Redistributable](http://go.microsoft.com/fwlink/?LinkId=46459).  
  
> [!NOTE]  
>  Assurez-vous que vous vous connectez avec les privilèges d'administrateur avant d'installer ce logiciel.  
  
## <a name="operating-system-requirements"></a>Système d'exploitation requis  
 Pour obtenir la liste des systèmes d’exploitation qui prennent en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, consultez [prennent en charge les stratégies de SQL Server Native Client](applications/support-policies-for-sql-server-native-client.md).  
  
## <a name="sql-server-requirements"></a>Configuration SQL Server requise  
 Pour utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client afin d'accéder aux données de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez avoir installé une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prend en charge les connexions à partir de toutes les versions de MDAC, Windows Data Access Components, et toutes les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Lorsqu'une version cliente plus ancienne se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les types de données de serveur inconnus du client sont mappés à des types compatibles avec la version du client. Pour plus d'informations, consultez Compatibilité des types de données pour les versions du client, plus loin dans cette rubrique.  
  
## <a name="cross-language-requirements"></a>Configuration multilingue  
 La version anglaise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est prise en charge sur toutes les versions localisées des systèmes d'exploitation pris en charge. Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sont prises en charge sur les systèmes d'exploitation localisés dans la même langue que la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client localisée. Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sont également prises en charge sur les versions en anglais des systèmes d'exploitation pris en charge, sous réserve que les paramètres de langue correspondants soient installés.  
  
 Pour les mises à niveau :  
  
-   Les versions en anglais de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peuvent être mises à niveau vers n'importe quelle version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peuvent être mises à niveau vers des versions localisées dans la même langue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   La version localisée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client peut être mise à niveau vers la version en anglais de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
-   Les versions localisées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ne peuvent pas être mises à niveau vers des versions localisées dans une autre langue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="data-type-compatibility-for-client-versions"></a>Compatibilité des types de données pour les versions du client  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappent les nouveaux types de données aux types de données plus anciens qui sont compatibles avec les clients de bas niveau, comme indiqué dans le tableau ci-dessous.  
  
 Les applications OLE DB et ADO peuvent utiliser le mot clé de chaîne de connexion `DataTypeCompatibility` avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client pour exploiter les types de données plus anciens. Lorsque `DataTypeCompatibility=80`, les clients OLE DB se connectent à l'aide de la version TDS (Tabular Data Stream) de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] plutôt que de la version TDS. Cela signifie que pour [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les types de données ultérieurs, la conversion de bas niveau sera effectuée par le serveur et non par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Cela signifie également que les fonctionnalités disponibles sur la connexion seront limitées à l'ensemble de fonctionnalités de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Plutôt que d'essayer de transmettre des requêtes non valides au serveur, une détection des tentatives d'utilisation de nouveaux types de données ou fonctionnalités intervient dès que possible sur les appels d'API et les erreurs sont retournées à l'application appelante.  
  
 Il n'y a pas de contrôle `DataTypeCompatibility` pour ODBC.  
  
 IDBInfo::GetKeywords retourne toujours une liste de mots clés qui correspond à la version du serveur sur la connexion et n’est pas affectée par `DataTypeCompatibility`.  
  
|Type de données|SQL Server Native Client<br /><br /> SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Windows Data Access Components, MDAC et<br /><br /> applications OLE DB SQL Server Native Client avec DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 Ko)|udt|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|image|  
|varchar(max)|varchar|varchar|Texte|  
|nvarchar(max)|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|Ntext|  
|CLR UDT (>= 8 Ko)|udt|varbinary|image|  
|Date|Date|varchar|Varchar|  
|datetime2|datetime2|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|Varchar|  
|time|time|varchar|Varchar|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](sql-server-native-client-programming.md)   
 [Installation de SQL Server Native Client](applications/installing-sql-server-native-client.md)  
  
  
