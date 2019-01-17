---
title: FULLTEXTSERVICEPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FULLTEXTSERVICEPROPERTY_TSQL
- FULLTEXTSERVICEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- FULLTEXTSERVICEPROPERTY function
- services [SQL Server], full-text search properties
- test
ms.assetid: b7dcacb0-af83-4807-9d1e-49148b56b59c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4fbdc84168ea3c0878924033347ca0c0fff3e514
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206158"
---
# <a name="fulltextserviceproperty-transact-sql"></a>FULLTEXTSERVICEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les propriétés du Moteur d'indexation et de recherche en texte intégral. Ces propriétés peuvent être définies et récupérées à l’aide de **sp_fulltext_service**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FULLTEXTSERVICEPROPERTY ('property')  
```  
  
## <a name="arguments"></a>Arguments  
 *property*  
 Expression contenant le nom de la propriété du niveau de service de recherche en texte intégral. Le tableau donne la liste des propriétés et fournit les descriptions des informations renvoyées.  
  
> [!NOTE]
>  Les propriétés suivantes seront supprimées dans une version future de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **ConnectTimeout**, **DataTimeout** et **ResourceUsage**. Évitez par conséquent d'utiliser ces propriétés dans un nouveau travail de développement et prévoyez la modification des applications qui les utilisent actuellement.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|**ResourceUsage**|Retourne 0. Pris en charge pour la compatibilité descendante uniquement.|  
|**ConnectTimeout**|Retourne 0. Pris en charge pour la compatibilité descendante uniquement.|  
|**IsFulltextInstalled**|Composant de texte intégral installé avec l'instance actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = Texte intégral non installé.<br /><br /> 1 = Texte intégral installé.<br /><br /> NULL = Entrée non valide ou erreur.|  
|**DataTimeout**|Retourne 0. Pris en charge pour la compatibilité descendante uniquement.|  
|**LoadOSResources**|Indique si les analyseurs lexicaux et les filtres du système d'exploitation sont enregistrés et utilisés avec cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, cette propriété est désactivée de façon à éviter tout changement de comportement intempestif suite à des mises à jour du système d'exploitation. Le fait d'utiliser les ressources du système d'exploitation permet d'accéder aux ressources associées aux langues et types de document enregistrés avec le service d'indexation [!INCLUDE[msCoName](../../includes/msconame-md.md)], mais cela n'implique pas l'installation des ressources propres à l'instance. Si vous activez le chargement des ressources du système d’exploitation, veillez à ce que ces ressources soient des binaires signés et approuvés. Sinon, les ressources ne peuvent pas être chargées quand la propriété **VerifySignature** est définie sur 1.<br /><br /> 0 = Utiliser uniquement les filtres et les analyseurs lexicaux propres à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = Charger les filtres et les analyseurs lexicaux du système d'exploitation.|  
|**VerifySignature**|Indique si seuls les binaires signés sont chargés par le service de Recherche [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Par défaut, seuls les binaires approuvés et signés sont chargés.<br /><br /> 0 = Ne pas vérifier si les binaires sont signés.<br /><br /> 1 = Vérifier que seuls les binaires approuvés et signés sont chargés.|  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant vérifie si seules les représentations binaires signées sont chargées, et la valeur de retour indique que cette vérification n'a pas lieu.  
  
```  
SELECT fulltextserviceproperty('VerifySignature');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
0  
```  
  
 Notez que pour réinitialiser la vérification de signature à sa valeur par défaut, soit 1, vous pouvez utiliser l'instruction `sp_fulltext_service` suivante :  
  
```  
EXEC sp_fulltext_service @action='verify_signature', @value=1;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)  
  
  
