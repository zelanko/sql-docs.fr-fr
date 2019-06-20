---
title: Section UserList du fichier de personnalisation | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- UserList section in rds [ADO]
- customization file in RDS [ADO]
ms.assetid: 42e8ec20-eaac-4a95-8cb8-4bba93a75bcb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e38b253cdebcc5ab976de8c8eb355f7f6fb03aec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699535"
---
# <a name="customization-file-userlist-section"></a>Fichier de personnalisation, section UserList
Le **userlist** section se rapporte à la **connecter** section avec la même *identificateur* paramètre.  
  
 Cette section peut contenir un *entrée d’accès utilisateur*, qui spécifie l’accès de droits pour l’utilisateur spécifié et remplace le *par défaut* *d’accéder à entrée* dans la mise en correspondance **connecter** section.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 Une entrée d’accès utilisateur est au format :  
  
 _userName_ **=**   
 **_accessRights_**  
  
|Élément|Description|  
|----------|-----------------|  
|*userName*|Le *nom d’utilisateur* de la personne utilisant cette connexion. Noms d’utilisateur valides sont établies avec IIS **Service Manager** boîte de dialogue.|  
|**_accessRights_**|L’un des droits d’accès suivants :<br /><br /> -   **NoAccess** -utilisateur ne peut pas accéder à la source de données.<br />-   **ReadOnly** -l’utilisateur peut lire la source de données.<br />-   **Lecture/écriture** -utilisateur capable de lire ou écrire dans la source de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de personnalisation, Section Connect](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Fichier de personnalisation, Section de journaux](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Fichier de personnalisation, Section SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Personnalisation de DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Paramètres Client requis](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Présentation du fichier de personnalisation](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Écriture d’un gestionnaire personnalisé](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


