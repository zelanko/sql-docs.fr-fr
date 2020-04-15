---
title: Travailler avec les notifications de requêtes (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8561d6c0e48e37dba7e22939fd868376c0ebdc9a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303222"
---
# <a name="working-with-query-notifications"></a>Utilisation de notifications de requêtes
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Les notifications de requêtes ont été introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Basées sur l'infrastructure de Service Broker introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], les notifications de requêtes permettent aux applications d'être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d'informations à partir d'une base de données, par exemple une application Web, et qui doivent être notifiées en cas de modification des données sources.  
  
 Les notifications de requêtes vous permettent de demander une notification dans un délai d'attente spécifié lorsque les données sous-jacentes d'une requête sont modifiées. La demande de notification spécifie les options de notification, notamment le nom du service, le texte du message et la valeur du délai d'attente au serveur. Les notifications sont remises par l'intermédiaire d'une file d'attente Service Broker qui peut être interrogée par les applications pour détecter les notifications disponibles.  
  
 La syntaxe de la chaîne des options de notifications de requêtes est :  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 Par exemple :  
  
 `service=mySSBService;local database=mydb`  
  
 La durée de vie des abonnements aux notifications est supérieure à celle des processus qui les initialisent. Cela s'explique par le fait qu'une application peut créer un abonnement aux notifications, puis se terminer. L'abonnement reste valide, et la notification a lieu si les données sont modifiées dans le délai d'attente imparti spécifié au moment de la création de l'abonnement. Une notification est identifiée par la requête exécutée, les options de notification et le texte du message, et peut être annulée en attribuant la valeur 0 au délai d'attente.  
  
 Les notifications sont envoyées une seule fois. Pour une notification continue des modifications de données, un nouvel abonnement doit être créé en exécutant à nouveau la requête une fois chaque notification traitée.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Les applications native Client reçoivent [!INCLUDE[tsql](../../../includes/tsql-md.md)] généralement des notifications en utilisant la commande [RECEIVE](../../../t-sql/statements/receive-transact-sql.md) pour lire les notifications de la file d’attente associée au service spécifié dans les options de notification.  
  
> [!NOTE]  
>  Les noms de tables doivent être qualifiés dans des requêtes pour lesquelles une notification est requise, par exemple `dbo.myTable`. Les noms de tables doivent être qualifiés avec des noms en deux parties. L'abonnement n'est pas valide si des noms en trois ou quatre parties sont utilisés.  
  
 L'infrastructure de notification repose sur une fonctionnalité de mise en file d'attente introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. En général, les notifications générées au niveau du serveur sont envoyées par l'intermédiaire de ces files d'attente pour un traitement ultérieur.  
  
 Pour utiliser des notifications de requêtes, une file d'attente et un service doivent exister sur le serveur. Vous pouvez les créer à l'aide d'une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] semblable à la suivante :  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  Le service doit utiliser le contrat prédéfini `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification`, comme indiqué plus haut.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur native De DB OLE de client prend en charge la notification des consommateurs sur la modification des rangées. Le consommateur reçoit la notification à chaque phase de la modification de l'ensemble de lignes et à chaque tentative de modification.  
  
> [!NOTE]  
>  Passer une requête en notifications au serveur avec **ICommand : : : Exécuter** est [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le seul moyen valable de s’abonner aux notifications de requête avec le fournisseur de DB OLE de client autochtone.  
  
### <a name="the-dbpropset_sqlserverrowset-property-set"></a>Le jeu de propriétés DBPROPSET_SQLSERVERROWSET  
 Afin d’appuyer les notifications de requête [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par l’intermédiaire d’OLE DB, Native Client ajoute les nouvelles propriétés suivantes à l’ensemble de propriétés DBPROPSET_SQLSERVERROWSET.  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Nombre de secondes pendant lesquelles la notification de requête doit rester active.<br /><br /> La valeur par défaut est 432 000 secondes (5 jours). La valeur minimale est 1 seconde, et la valeur maximale est 2^31-1 secondes.|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Texte du message de la notification. Il est défini par l'utilisateur et n'a aucun format prédéfini.<br /><br /> Par défaut, la chaîne est vide. Vous pouvez spécifier un message à l'aide de 1-2000 caractères.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Options de notification de requêtes. Ceux-ci sont spécifiés dans une chaîne avec la syntaxe*de valeur* *de nom.*= L'utilisateur est chargé de créer le service et de lire les notifications de la file d'attente.<br /><br /> La valeur par défaut est une chaîne vide.|  
  
 L'abonnement aux notifications est toujours validé, que l'instruction ait été exécutée dans une transaction utilisateur ou en mode de validation automatique, ou que la transaction dans laquelle l'instruction s'est exécutée ait été validée ou restaurée. La notification du serveur est déclenchée lorsque l'une des conditions de notification non valides suivantes se produit : modification des données sous-jacentes ou du schéma ou expiration du délai d'attente imparti (selon l'opération qui se produit en premier). Les inscriptions de notification sont supprimées dès qu'elles sont déclenchées. Par conséquent, lorsque l'application reçoit des notifications, l'application doit encore s'abonner au cas où elle souhaiterait obtenir d'autres mises à jour.  
  
 Une autre connexion ou un autre thread peut vérifier la file d'attente de destination pour les notifications. Par exemple :  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 Notez que SELECT * ne supprime pas l’entrée de la file d’attente, contrairement à RECEIVE \* FROM. Cela bloque un thread serveur si la file d'attente est vide. S'il existe des entrées de file d'attente au moment de l'appel, elles sont retournées immédiatement ; sinon, l'appel attend qu'une entrée de file d'attente soit soumise.  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 Cette instruction retourne immédiatement un jeu de résultats vide si la file d'attente est vide ; sinon, elle retourne toutes les notifications de la file d'attente.  
  
 Si SSPROP_QP_NOTIFICATION_MSGTEXT et SSPROP_QP_NOTIFICATION_OPTIONS ne sont pas NULL et ne sont pas vides, l'en-tête TDS de notifications de requêtes contenant les trois propriétés définies plus haut sont envoyées au serveur avec chaque exécution de la commande. Si l'un d'eux est NULL (ou vide), l'en-tête n'est pas envoyé et DB_E_ERRORSOCCURRED est déclenché (ou DB_S_ERRORSOCCURRED si les propriétés sont toutes deux marquées comme étant facultatives) et la valeur d'état est DBPROPSTATUS_BADVALUE. La validation se produit dans la phase de préparation et d'exécution. De la même façon, DB_S_ERRORSOCCURED est déclenché quand les propriétés de notification de requête sont définies pour les connexions sur les versions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] La valeur d'état dans ce cas est DBPROPSTATUS_NOTSUPPORTED.  
  
 L'initialisation d'un abonnement ne garantit pas que les messages suivants soient correctement remis. De plus, aucun contrôle n'est effectué en termes de validité du nom du service spécifié.  
  
> [!NOTE]  
>  La préparation d'instructions ne provoque jamais l'initialisation de l'abonnement ; seule l'exécution d'instructions peut y parvenir et les notifications de requêtes ne sont pas concernées par l'utilisation des services principaux OLE DB.  
  
 Pour plus d’informations sur l’ensemble de propriétés DBPROPSET_SQLSERVERROWSET, voir [Rowset Properties and Behaviors](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur de Native Client ODBC prend en charge les notifications de requêtes par l’ajout de trois nouveaux attributs aux fonctions [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) et [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) :  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
  
 Si SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT et SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS ne sont pas NULL, l'en-tête TDS de notifications de requêtes contenant les trois attributs définis plus haut sera envoyé au serveur chaque fois que la commande est exécutée. Si l'un d'eux est Null, l'en-tête n'est pas envoyé, et SQL_SUCCESS_WITH_INFO est retourné. La validation se fait sur [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360), **SqlExecDirect**, et **SqlExecute**, qui échouent tous si les attributs ne sont pas valides. De la même façon, lorsque ces attributs de notification de requête sont définis pour les versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], l'exécution échoue avec SQL_SUCCESS_WITH_INFO.  
  
> [!NOTE]  
>  La préparation d'instructions ne provoque jamais l'initialisation de l'abonnement ; l'abonnement peut être initialisé par l'exécution d'instructions.  
  
## <a name="special-cases-and-restrictions"></a>Cas particuliers et restrictions  
 Les types de données suivants ne sont pas pris en charge pour les notifications :  
  
-   **text**  
  
-   **ntext**  
  
-   **Image**  
  
 Si une demande de notification est soumise pour une requête qui retourne l'un de ces types, la notification se déclenche immédiatement en spécifiant que l'abonnement aux notifications n'était pas possible.  
  
 Si une demande d'abonnement est soumise pour un lot ou une procédure stockée, une demande d'abonnement séparée est soumise pour chaque instruction exécutée dans le traitement ou la procédure stockée. Les instructions EXECUTE n'inscrivent aucune notification mais la demande de notification est envoyée à la commande exécutée. S'il s'agit d'un lot, le contexte est appliqué aux instructions exécutées et les mêmes règles décrites ci-dessus sont appliquées.  
  
 La soumission d’une requête pour notification qui a été soumise par le même utilisateur dans le même contexte de base de données et qui a le même modèle, les mêmes valeurs de paramètres, le même IDENTIFIANT de notification et le même emplacement de livraison d’un abonnement actif existant, renouvellera l’abonnement existant, réinitialisant le nouveau délai spécifié. Cela signifie que si une notification est demandée pour des requêtes identiques, une seule notification sera envoyée. Cette situation concerne une requête dupliquée dans un lot ou une requête dans une procédure stockée qui a été appelée plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
