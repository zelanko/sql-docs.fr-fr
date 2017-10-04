---
title: "CRÉER une SESSION de DIAGNOSTICS (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71f3463ad4d91bd117c322e9e63c0b331b07ca9f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-diagnostics-session-transact-sql"></a>CRÉER une SESSION de DIAGNOSTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Les sessions de diagnostic permettent d’enregistrer les informations de diagnostic détaillées, défini par l’utilisateur sur les performances du système ou de la requête.  
  
 Les sessions de diagnostic sont généralement utilisées pour déboguer des performances d’une requête spécifique, ou pour surveiller le comportement d’un composant matériel spécifique au cours de l’opération de l’appliance.  
  
> [!NOTE]  
>  Vous devez être familiarisé avec XML pour pouvoir utiliser les sessions de diagnostic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Creating a new diagnostics session:  
CREATE DIAGNOSTICS SESSION diagnostics_name AS N’{<session_xml>}’;  
  
<session_xml>::  
<Session>  
   [ <MaxItemCount>max_item_count_num</MaxItemCount> ]  
   <Filter>  
      { \<Event Name=”event_name”/>  
         [ <Where>\<filter_property_name Name=”value” ComparisonType="comp_type"/></Where> ] [ ,...n ]  
      } [ ,...n ]  
   </Filter> ]   
   <Capture>  
      \<Property Name=”property_name”/> [ ,...n ]  
   </Capture>  
<Session>  
  
Retrieving results for a diagnostics session:  
SELECT * FROM master.sysdiag.diagnostics_name ;  
  
Removing results for a diagnostics session:  
DROP DIAGNOSTICS SESSION diagnostics_name ;  
```  
  
## <a name="arguments"></a>Arguments  
 *diagnostics_name*  
 Le nom de la session de diagnostic. Nom de session de diagnostics peut inclure des caractères a-z, A-Z et 0-9. En outre, les noms de session de diagnostics doivent commencer par un caractère. *diagnostics_name* est limitée à 127 caractères.  
  
 *max_item_count_num*  
 Le nombre d’événements devant être persistantes dans une vue. Par exemple, si 100 est spécifié, les 100 derniers événements correspondant aux critères de filtre sont rendues persistantes dans la session de diagnostic. Si moins de 100 événements sont trouvés, la session de diagnostic contient moins de 100 événements. *max_item_count_num* doit être au moins 100 et inférieur ou égal à 100 000.  
  
 *nom_événement*  
 Définit les événements réels à recueillir dans la session de diagnostic.  *nom_événement* est un des événements répertoriés dans [sys.pdw_diag_events](http://msdn.microsoft.com/en-us/d813aac0-cea1-4f53-b8e8-d26824bc2587) où `sys.pdw_diag_events.is_enabled='True'`.  
  
 *filter_property_name*  
 Le nom de la propriété auquel limiter les résultats. Par exemple, si vous souhaitez limiter en fonction de l’id de session, *filter_property_name* doit être *SessionId*. Consultez *property_name* ci-dessous pour obtenir la liste de valeurs potentielles pour *filter_property_name*.  
  
 *valeur*  
 Une valeur à évaluer par rapport à *filter_property_name*. Le type de valeur doit correspondre au type de propriété. Par exemple, si le type de propriété est de type decimal, type de *valeur* doit être décimale.  
  
 *comp_type*  
 Le type de comparaison. Potentiels valeurs sont : égal à, EqualsOrGreaterThan, EqualsOrLessThan, GreaterThan, LessThan, NotEquals, Contains, expression régulière  
  
 *property_name*  
 Une propriété associée à l’événement.  Noms de propriété peuvent faire partie de la balise de capture ou utilisées dans le cadre des critères de filtrage.  
  
|Nom de la propriété| Description|  
|-------------------|-----------------|  
|UserName|Un nom d’utilisateur (connexion).|  
|SessionId|Un ID de session.|  
|QueryId|Un ID de requête.|  
|CommandType|Un type de commande.|  
|CommandText|Texte dans une commande de traitement.|  
|OperationType|Le type d’opération pour l’événement.|  
|Duration|La durée de l’événement.|  
|SPID|L’ID de processus de Service.|  
  
## <a name="remarks"></a>Notes  
 Chaque utilisateur est autorisé à un maximum de 10 sessions simultanées de diagnostics. Consultez [sys.pdw_diag_sessions](http://msdn.microsoft.com/en-us/ca111ddc-2787-4205-baf0-1a242c0257a9) pour obtenir la liste des sessions actives et les inutiles des sessions à l’aide de drop `DROP DIAGNOSTICS SESSION`.  
  
 Les sessions de diagnostic continue à collecter les métadonnées jusqu'à ce que supprimée.  
  
## <a name="permissions"></a>Permissions  
 Requiert le **ALTER SERVER STATE** autorisation.  
  
## <a name="locking"></a>Verrouillage  
 Acquiert un verrou partagé sur la table des Sessions de Diagnostic.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-diagnostics-session"></a>A. Création d’une session de diagnostic  
 Cet exemple crée une session de diagnostic pour enregistrer des métriques de performances du moteur de base de données. L’exemple crée une session de diagnostic qui écoute les événements en cours d’exécution et de fin de requête de moteur et un événement de blocage de DMS. Ce qui est retourné est le texte de commande, nom de l’ordinateur, id de demande (id de requête) et l’événement a été créé sur la session.  
  
```  
CREATE DIAGNOSTICS SESSION MYDIAGSESSION AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:EngineQueryRunningEvent" />  
      <Event Name="DmsCoreInstrumentation:DmsBlockingQueueEnqueueBeginEvent" />  
      <Where>  
         <SessionId Value="381" ComparisonType="NotEquals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Query.CommandText" />  
      <Property Name="MachineName" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Alias" />  
      <Property Name="Duration" />  
      <Property Name="Session.SessionId" />  
   </Capture>  
</Session>';  
```  
  
 Après la création de la session de diagnostic, exécutez une requête.  
  
```  
SELECT COUNT(EmployeeKey) FROM AdventureWorksPDW2012..FactSalesQuota;  
```  
  
 Puis affichez les résultats de la session de diagnostic en sélectionnant à partir du schéma sysdiag.  
  
```  
SELECT * FROM master.sysdiag.MYDIAGSESSION;  
```  
  
 Notez que le schéma sysdiag contient une vue qui porte le nom de votre session de diagnostic.  
  
 Pour afficher uniquement l’activité de votre connexion, ajoutez le `Session.SPID` propriété et ajoutez `WHERE [Session.SPID] = @@spid;` à la requête.  
  
 Lorsque vous avez terminé avec la session de diagnostic, la supprimer à l’aide de la **supprimer les DIAGNOSTICS** commande.  
  
```  
DROP DIAGNOSTICS SESSION MYDIAGSESSION;  
```  
  
### <a name="b-alternative-diagnostic-session"></a>B. Autre session de diagnostic  
 Deuxième exemple avec des propriétés légèrement différentes.  
  
```  
-- Determine the session_id of your current session  
SELECT TOP 1 session_id();  
-- Replace \<*session_number*> in the code below with the numbers in your session_id  
CREATE DIAGNOSTICS SESSION PdwOptimizationDiagnostics AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:MemoGenerationBeginEvent" />  
      <Event Name="EngineInstrumentation:MemoGenerationEndEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationBeginEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationEndEvent" />  
      <Event Name="DSQLInstrumentation:BuildRelOpContextTreeBeginEvent" />  
      <Event Name="DSQLInstrumentation:PostPlanGenModifiersEndEvent" />  
      <Where>  
         <SessionId Value="\<*session_number*>" ComparisonType="Equals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Session.SessionId" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Query.CommandText" />  
      <Property Name="Name" />  
      <Property Name="DateTimePublished" />  
      <Property Name="DateTimePublished.Ticks" />  
  </Capture>  
</Session>';  
```  
  
 Exécutez une requête, telles que :  
  
```  
USE ssawPDW;  
GO  
SELECT * FROM dbo.FactFinance;  
```  
  
 La requête suivante retourne la durée d’autorisation :  
  
```  
SELECT *   
FROM master.sysdiag.PdwOptimizationDiagnostics   
ORDER BY DateTimePublished;  
```  
  
 Lorsque vous avez terminé avec la session de diagnostic, la supprimer à l’aide de la **supprimer les DIAGNOSTICS** commande.  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  
