---
title: "Connexion à une base de données SQL Azure Windows à l’aide de SQL Server Native Client | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: native-client|applications
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d4131808a9c5bbf400c0109606b4d1c76396f193
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>Connexion à une base de données Microsoft Azure SQL Database à l'aide de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Pour obtenir un exemple qui montre comment se connecter à un [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] à l’aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, consultez [développement : rubriques de procédures (base de données Windows Azure SQL)](http://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problèmes connus lors de la connexion à une base de données SQL  
 Voici les problèmes connus liés à la connexion à une [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   Une connexion établie avec **SQLBrowseConnect** peut être rejeté se **SQLBrowseConnect** est utilisé dans les étapes.  Supposons que le nom du pilote est transmis dans le premier appel, le serveur et les informations d'identification (utilisateur et mot de passe) sont envoyés dans le deuxième appel, établissant la connexion, et un nom de base de données et un langage sont envoyés dans le troisième appel.  Le troisième appel indique à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client d'émettre une instruction USE pour modifier les bases de données. Toutefois, l'instruction USE n'est pas prise en charge dans [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], ce qui génère l'erreur suivante :  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
