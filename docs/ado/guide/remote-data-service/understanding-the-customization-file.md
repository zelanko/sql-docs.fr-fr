---
title: Présentation du fichier de personnalisation | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 581065868f408eca28f15ffe9fb703d53e16ae66
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704134"
---
# <a name="understanding-the-customization-file"></a>Présentation du fichier de personnalisation
Chaque en-tête de section dans le fichier de personnalisation se compose de crochets ( **[]** ) contenant un type et un paramètre. Les quatre types de section sont indiquées par les chaînes littérales **connecter**, **sql**, **userlist**, ou **journaux**. Le paramètre est la chaîne littérale, la valeur par défaut, un identificateur spécifié par l’utilisateur ou rien du tout.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Par conséquent, chaque section est marquée avec l’un des en-têtes de section suivants :  
  
```console
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 Les en-têtes de section des éléments suivants.  
  
|Élément|Description|  
|----------|-----------------|  
|**connect**|Une chaîne littérale qui modifie une chaîne de connexion.|  
|**sql**|Une chaîne littérale qui modifie une chaîne de commande.|  
|**userlist**|Une chaîne littérale qui modifie les droits d’accès d’un utilisateur spécifique.|  
|**logs**|Une chaîne littérale qui spécifie un fichier journal de l’enregistrement d’erreurs opérationnelles.|  
|**default**|Une chaîne littérale qui est utilisée si aucun identificateur n’est spécifié ou trouvé.|  
|*identifier*|Chaîne qui correspond à une chaîne dans le **connecter** ou **commande** chaîne.<br /><br /> -Utilisez cette section si l’en-tête de section contient **connecter** et la chaîne d’identificateur se trouve dans la chaîne de connexion.<br />-Utilisez cette section si l’en-tête de section contient **sql** et la chaîne d’identificateur se trouve dans la chaîne de commande.<br />-Utilisez cette section si l’en-tête de section contient **userlist** et la chaîne de l’identificateur correspond à un **connecter** identificateur de section.|  
  
 Le **DataFactory** appelle le gestionnaire, en passant les paramètres client. Le gestionnaire recherche les chaînes entières dans les paramètres client qui correspondent aux identificateurs dans les en-têtes de la section appropriée. Si une correspondance est trouvée, le contenu de cette section est appliqué au paramètre du client.  
  
 Une section particulière est utilisée dans les circonstances suivantes :  
  
-   A **connecter** section est utilisée si la valeur du client de connexion mot clé de chaîne, «**Source de données =** _valeur_», correspond à un **connecter** identificateur de la section *.*  
  
-   Un **sql** section est utilisée si la chaîne de commande client contient une chaîne qui correspond à un **sql** identificateur de section.  
  
-   Un **connecter** ou **sql** section avec un paramètre par défaut est utilisée si aucun identificateur correspondant.  
  
-   Un **userlist** section est utilisée si le **userlist** section identificateur correspondances un **connecter** identificateur de la section. S’il existe une correspondance, le contenu de la **userlist** section sont appliqués à la connexion régie par le **connecter** section.  
  
-   Si la chaîne dans une chaîne de connexion ou de commande ne correspond pas à l’identificateur dans les **connecter** ou **sql** section d’en-tête et il est aucun **connecter** ou **sql**  section d’en-tête avec un paramètre par défaut, la chaîne du client est utilisé sans modification.  
  
-   Le **journaux** section est utilisée chaque fois que le **DataFactory** est en cours.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section Connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Fichier de personnalisation, Section de journaux](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Fichier de personnalisation, Section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Fichier de personnalisation, Section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

