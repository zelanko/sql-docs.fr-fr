---
title: "CRÉER le SERVICE (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVICE_TSQL
- SERVICE
- CREATE SERVICE
- SERVICE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- services [Service Broker], creating
- CREATE SERVICE statement
- contracts [Service Broker], service creation
ms.assetid: fb804fa2-48eb-4878-a12f-4e0d5f4bc9e3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5298494b6c3be0685df771f6d86e11c7b788d002
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-service-transact-sql"></a>CREATE SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un nouveau service. Un service [!INCLUDE[ssSB](../../includes/sssb-md.md)] est un nom pour une tâche ou un ensemble de tâches spécifiques. [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise le nom du service pour acheminer les messages, les remettre à la file d'attente appropriée dans une base de données et appliquer le contrat pour une conversation.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE SERVICE service_name  
   [ AUTHORIZATION owner_name ]  
   ON QUEUE [ schema_name. ]queue_name  
   [ ( contract_name | [DEFAULT][ ,...n ] ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *SERVICE_NAME*  
 Nom du service à créer. Un nouveau service est créé dans la base de données active et il appartient au principal spécifié dans la clause AUTHORIZATION. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés. Le *service_name* doit être un **sysname**.  
  
> [!NOTE]  
>  Ne créez pas un service qui utilise le mot clé ANY pour le *service_name*. Lorsque vous spécifiez ANY pour un nom de service dans CREATE BROKER PRIORITY, la priorité est considérée pour tous les services. Elle n'est pas limitée à un service dont le nom est ANY.  
  
 AUTORISATION *owner_name*  
 Définit le propriétaire du service comme étant l'utilisateur ou le rôle de la base de données spécifié. Lorsque l’utilisateur actuel est **dbo** ou **sa**, *owner_name* peut être le nom de n’importe quel utilisateur ou rôle valide. Dans le cas contraire, *owner_name* doit être le nom de l’utilisateur actuel, le nom d’un utilisateur de l’utilisateur actuel possède l’autorisation IMPERSONATE ou le nom d’un rôle auquel appartient l’utilisateur actuel.  
  
 File d’attente ON [ *nom_schéma***.** ] *nom_file_attente*  
 Spécifie la file d'attente qui reçoit les messages pour le service. Cette file d'attente doit exister dans la même base de données que celle du service. Si aucun *schema_name* est fourni, le schéma est le schéma par défaut pour l’utilisateur qui exécute l’instruction.  
  
 *nom_contract*  
 Spécifie un contrat pour lequel ce service peut être une cible. Les programmes de service initient des conversations avec le service à l'aide des contrats spécifiés. Si aucun contrat n'est précisé, le service peut seulement initier des conversations.  
  
 **[**PAR DÉFAUT**]**  
 Indique que le service peut être une cible pour des conversations respectant le contrat DEFAULT. Dans le contexte de cette clause, DEFAULT n'est pas un mot clé et il doit être délimité comme un identificateur. Le contrat DEFAULT autorise les deux côtés de la conversation à envoyer des messages de type DEFAULT. Le type de message DEFAULT utilise la validation NONE.  
  
## <a name="remarks"></a>Notes  
 Un service expose les fonctionnalités fournies par les contrats avec lesquels il est associé, pour qu'ils puissent être utilisés par d'autres services. L'instruction CREATE SERVICE spécifie les contrats pour lesquels ce service est la cible. Un service est une cible exclusivement pour les conversations qui utilisent les contrats spécifiés par le service. Un service qui ne spécifie aucun contrat n'expose aucune fonctionnalité aux autres services.  
  
 Les conversations lancées à partir de ce service peuvent utiliser n'importe quel contrat. Vous créez un service sans spécifier de contrat lorsque le service initie seulement des conversations.  
  
 Lorsque [!INCLUDE[ssSB](../../includes/sssb-md.md)] accepte une nouvelle conversation d'un service distant, le nom du service cible détermine la file d'attente où Service Broker place les messages dans la conversation.  
  
## <a name="permissions"></a>Permissions  
 L’autorisation de création d’un service par défaut aux membres de la **db_ddladmin** ou **db_owner** des rôles de base de données fixes et **sysadmin** rôle serveur fixe. L'utilisateur exécutant l'instruction CREATE SERVICE doit disposer de l'autorisation REFERENCES pour la file d'attente et tous les contrats spécifiés.  
  
 L’autorisation REFERENCES pour un service par défaut est le propriétaire du service, les membres de la **db_ddladmin** ou **db_owner** fixe des rôles de base de données et les membres de la **sysadmin** rôle serveur fixe. Autorisations SEND pour un paramètre par défaut au propriétaire du service, les membres du **db_owner** fixe du rôle de base de données et les membres de la **sysadmin** rôle serveur fixe.  
  
 Un service ne peut pas être un objet temporaire. Service de noms commençant par  **#**  sont autorisées, mais sont des objets permanents.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-service-with-one-contract"></a>A. Création d'un service avec un contrat  
 L'exemple suivant crée le service `//Adventure-Works.com/Expenses` dans la file d'attente `ExpenseQueue` du schéma `dbo`. Les dialogues qui ciblent ce service doivent respecter le contrat `//Adventure-Works.com/Expenses/ExpenseSubmission`.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE [dbo].[ExpenseQueue]  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="b-creating-a-service-with-multiple-contracts"></a>B. Création d'un service avec plusieurs contrats  
 L'exemple suivant crée le service `//Adventure-Works.com/Expenses` dans la file d'attente `ExpenseQueue`. Les dialogues qui ciblent ce service doivent respecter le contrat `//Adventure-Works.com/Expenses/ExpenseSubmission` ou le contrat `//Adventure-Works.com/Expenses/ExpenseProcessing`.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue  
    ([//Adventure-Works.com/Expenses/ExpenseSubmission],  
     [//Adventure-Works.com/Expenses/ExpenseProcessing]) ;  
```  
  
### <a name="c-creating-a-service-with-no-contracts"></a>C. Création d'un service sans contrat  
 L’exemple suivant crée le service `//Adventure-Works.com/Expenses on the ExpenseQueue` file d’attente. Ce service ne possède pas d'informations de contrat. Par conséquent, il ne peut être que l'initiateur d'un dialogue.  
  
```  
CREATE SERVICE [//Adventure-Works.com/Expenses] ON QUEUE ExpenseQueue ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SERVICE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-transact-sql.md)   
 [DROP SERVICE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
