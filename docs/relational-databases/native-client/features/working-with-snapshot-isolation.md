---
title: Utilisation de l’isolement de capture instantanée | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e95e7de3777bd0de64a42c4b01dfb5c7b96c4542
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719617"
---
# <a name="working-with-snapshot-isolation"></a>Utilisation de l’isolement de capture instantanée
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], un nouveau niveau d'isolement d'« instantané » a été introduit pour améliorer la concurrence pour les applications de traitement transactionnel en ligne (OLTP). Dans les versions antérieures à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la concurrence était uniquement basée sur le verrouillage, ce qui pouvait provoquer des problèmes de blocage pour certaines applications. Le niveau d'isolement d'instantané, qui dépend des améliorations apportées au contrôle de version de ligne, est conçu pour améliorer les performances en évitant les scénarios de blocage du lecteur/enregistreur.  
  
 Les transactions qui démarrent avec un niveau d'isolement d'instantané lisent un instantané de base de données au moment du démarrage de la transaction. Entre autres conséquences, lorsque vous ouvrez des curseurs de jeu de clés, dynamiques et côté serveur statiques dans un contexte de transaction d'instantané, ceux-ci se comportent de manière comparable à des curseurs statiques ouverts dans des transactions sérialisables. Toutefois, lorsque les curseurs sont ouverts avec un niveau d'isolement d'instantané, les verrous ne sont pas pris, ce qui peut réduire le blocage sur le serveur.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client a des améliorations qui tirent parti de l’isolation d’instantané introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] . Ces améliorations incluent des modifications aux jeux de propriétés DBPROPSET_DATASOURCEINFO et DBPROPSET_SESSION.  
  
### <a name="dbpropset_datasourceinfo"></a>DBPROPSET_DATASOURCEINFO  
 Le jeu de propriétés DBPROPSET_DATASOURCEINFO a été modifié pour indiquer que le niveau d'isolement d'instantané est pris en charge par l'ajout de la valeur DBPROPVAL_TI_SNAPSHOT utilisée dans la propriété DBPROP_SUPPORTEDTXNISOLEVELS. Cette nouvelle valeur indique que le niveau d'isolement d'instantané est pris en charge, que le contrôle de version ait été activé sur la base de données ou non. Voici une liste des valeurs DBPROP_SUPPORTEDTXNISOLEVELS :  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_SUPPORTEDTXNISOLEVELS|Type : VT_I4<br /><br /> Lecture/écriture : lecture seule<br /><br /> Description : masque de bits spécifiant les niveaux d'isolation de la transaction pris en charge. Combinaison de zéro ou plusieurs des éléments suivants :<br /><br /> DBPROPVAL_TI_CHAOS<br /><br /> DBPROPVAL_TI_READUNCOMMITTED<br /><br /> DBPROPVAL_TI_BROWSE<br /><br /> DBPROPVAL_TI_CURSORSTABILITY<br /><br /> DBPROPVAL_TI_READCOMMITTED<br /><br /> DBPROPVAL_TI_REPEATABLEREAD<br /><br /> DBPROPVAL_TI_SERIALIZABLE<br /><br /> DBPROPVAL_TI_ISOLATED<br /><br /> DBPROPVAL_TI_SNAPSHOT|  
  
### <a name="dbpropset_session"></a>DBPROPSET_SESSION  
 Le jeu de propriétés DBPROPSET_SESSION a été modifié pour indiquer que le niveau d'isolement d'instantané est pris en charge par l'ajout de la valeur DBPROPVAL_TI_SNAPSHOT utilisée dans la propriété DBPROP_SESS_AUTOCOMMITISOLEVELS. Cette nouvelle valeur indique que le niveau d'isolement d'instantané est pris en charge, que le contrôle de version ait été activé sur la base de données ou non. Voici une liste des valeurs DBPROP_SESS_AUTOCOMMITISOLEVELS :  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Type : VT_I4<br /><br /> Lecture/écriture : lecture seule<br /><br /> Description : spécifie un masque de bits qui indique le niveau d'isolation de la transaction lorsqu'elle se trouve en mode de validation automatique. Les valeurs pouvant être définies dans ce masque de bits sont les mêmes que celles qui peuvent être définies pour DBPROP_SUPPORTEDTXNISOLEVELS.|  
  
> [!NOTE]  
>  Les erreurs DB_S_ERRORSOCCURRED ou DB_E_ERRORSOCCURRED se produisent si DBPROPVAL_TI_SNAPSHOT est défini dans le cadre de l'utilisation de versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Pour plus d'informations sur la prise en charge du niveau d'isolement d'instantané dans les transactions, consultez [Prise en charge des transactions locales](../../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge l’isolement d’instantané grâce aux améliorations apportées aux fonctions [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) et [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) .  
  
### <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
 La fonction **SQLSetConnectAttr** prend désormais en charge l’utilisation de l’attribut SQL_COPT_SS_TXN_ISOLATION. L'attribution de la valeur SQL_TXN_SS_SNAPSHOT à SQL_COPT_SS_TXN_ISOLATION indique que la transaction aura lieu avec le niveau d'isolement d'instantané.  
  
### <a name="sqlgetinfo"></a>SQLGetInfo  
 La fonction [SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md) prend désormais en charge la valeur SQL_TXN_SS_SNAPSHOT ajoutée au type d’informations SQL_TXN_ISOLATION_OPTION.  
  
 Pour plus d’informations sur la prise en charge de l’isolement d’instantané dans les transactions, consultez [niveau d’isolement des transactions de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [Propriétés et comportements de l'ensemble de lignes](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
