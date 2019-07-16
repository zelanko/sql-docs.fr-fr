---
title: Solutions pour accéder aux données à distance | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS [ADO]
ms.assetid: d311cc67-7db7-4c43-9590-d465564695e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40485562c8385e05ced033062563d5c5165218de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922177"
---
# <a name="solutions-for-remote-data-access"></a>Solutions pour le service RDA (Remote Data Access)
## <a name="the-issue"></a>Le problème  
 ADO permet à votre application directement accéder à et modifier des sources de données (parfois appelés un système à deux niveaux). Par exemple, si votre connexion est à la source de données qui contient vos données, qui est une connexion directe dans un système à deux niveaux.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Toutefois, vous souhaiterez accéder indirectement aux sources de données via un intermédiaire tel que Microsoft® Internet Information Services (IIS). Cette disposition est parfois appelée un système à trois niveaux. IIS est un système client/serveur qui offre un moyen efficace pour une application locale ou un client appeler un programme distant ou serveur, via Internet ou un intranet. Le programme serveur parvient à accéder à la source de données et éventuellement traite les données acquises.  
  
 Par exemple, votre page Web d’intranet contient une application écrite en Microsoft® Visual Basic Scripting Edition (VBScript), qui se connecte à IIS. IIS à son tour se connecte à la source de données, récupère les données, il traite d’une certaine façon, puis retourne les informations traitées à votre application.  
  
 Dans cet exemple, votre application jamais directement connecté à la source de données ; IIS a fait. Et IIS accédé aux données au moyen d’ADO.  
  
> [!NOTE]
>  L’application client/serveur ne devra pas être basée sur Internet ou un intranet (autrement dit, basée sur le Web)-il pourrait se composer uniquement des programmes compilés sur un réseau local. Toutefois, le cas par défaut est une application basée sur le Web.  
  
 Car certains contrôles visuels, comme une grille, une case à cocher ou une liste, peuvent utiliser les informations retournées, les informations retournées doivent être facilement utilisées par un contrôle visuel.  
  
 Vous souhaitez une interface de programmation d’applications simple et efficace qui prend en charge les systèmes à trois niveaux et retourne des informations en tant que facilement comme s’il avait été récupéré sur un système à deux niveaux. Service de données à distance (RDS) est cette interface.  
  
## <a name="the-solution"></a>La solution  
 RDS définit un modèle de programmation - la séquence d’activités nécessaires pour accéder à et mettre à jour une source de données - pour accéder aux données via un intermédiaire, telles que les Services Internet (IIS). Le modèle de programmation résume toutes les fonctionnalités de RDS.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de programmation RDS de base](../../../ado/guide/remote-data-service/basic-rds-programming-model.md)   
 [Scénario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilisation et sécurité de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


