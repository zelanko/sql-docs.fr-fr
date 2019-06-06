---
title: Fichier de personnalisation, Section Connect | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c9ec47ffb89724e8a7991dae1d2296aa813e0c5e
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704315"
---
# <a name="customization-file-connect-section"></a>Fichier de personnalisation, section connect
Le comportement par défaut du gestionnaire consiste à refuser toutes les connexions. Le **connecter** section indique les exceptions à ce comportement. Par exemple, si tous les **connecter** sections sont absents ou vides, puis par défaut aucune connexion n’a pu être établie.  
  
 Le **connecter** section peut contenir :  
  
-   Une entrée d’accès par défaut qui spécifie la valeur par défaut lisent et écrivent les opérations autorisées sur cette connexion. S’il n’existe aucune entrée d’accès par défaut dans la section, la section sera ignorée.  
  
-   Nouvelle chaîne de connexion qui remplace la chaîne de connexion du client.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 Une entrée d’accès par défaut est au format :  
  
```console
  
Access=  
accessRight  
  
```  
  
 Une entrée de chaîne de connexion de remplacement est au format :  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Notes  
  
|Élément|Description|  
|----------|-----------------|  
|**Se connecter**|Une chaîne littérale qui indique qu’il est une entrée de chaîne de connexion.|  
|**_connectionString_**|Chaîne qui remplace la chaîne de connexion client global.|  
|**Accès**|Une chaîne littérale qui indique qu’il est une entrée d’accès.|  
|**_accessRight_**|L’un des droits d’accès suivants :<br /><br /> -   **NoAccess** -utilisateur ne peut pas accéder à la source de données.<br />-   **ReadOnly** -l’utilisateur peut lire la source de données.<br />-   **Lecture/écriture** -utilisateur capable de lire ou écrire dans la source de données.|  
  
 Si vous souhaitez autoriser toute connexion (en le désactivant, le comportement du gestionnaire par défaut), définissez l’entrée d’accès le **connecter par défaut** section à `Access=ReadWrite`et supprimez ou commentez à n’importe quel autre **connecter** _identificateur_ section.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section de journaux](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Fichier de personnalisation, Section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Fichier de personnalisation, Section UserList](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



