---
title: Boîte de dialogue Propriétés du DataSet, paramètres (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10023"
ms.assetid: 3a0672ad-c969-455b-b952-585164ce1dda
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 207aa0b0657670d93dbdfc92b80a0c3d3285de7d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030200"
---
# <a name="dataset-properties-dialog-box-parameters-report-builder"></a>Boîte de dialogue Propriétés du dataset, Paramètres (Générateur de rapports)
  Sélectionnez **paramètres** sur le **propriétés du Dataset** boîte de dialogue pour ajouter, modifier et supprimer des paramètres de requête.  
  
 Pour un dataset incorporé, les options s'appliquent au dataset dans la définition de rapport.  
  
 Pour un dataset partagé, les options s'appliquent à la définition de dataset partagé sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [Datasets incorporés et partagés &#40;Générateur de rapports et SSRS&#41;](report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Ajoutez un nouveau paramètre à la liste.  
  
 **Supprimer**  
 Supprimez le paramètre sélectionné de la liste.  
  
 **Flèche haut**  
 Déplacez le paramètre sélectionné vers le haut de la liste.  
  
 **Flèche bas**  
 Déplacez le paramètre sélectionné vers le bas de la liste.  
  
 **Nom du paramètre**  
 Tapez le nom d’un paramètre de requête que vous avez ajouté au dataset sous l’onglet **Requête** de la boîte de dialogue **Propriétés du dataset** .  
  
 **Valeur du paramètre**  
 Pour les datasets incorporés uniquement.  
  
 Entrez une valeur pour le paramètre de requête. Il peut s'agir d'une valeur statique ou d'une expression faisant référence à un objet présent dans le rapport ; toutefois, elle ne peut pas faire référence à des éléments de rapport ou des champs. Par défaut, **Valeur** contient une expression qui pointe vers un paramètre de rapport.  
  
 **Valeur par défaut**  
 Pour les datasets partagés uniquement.  
  
 Activez la case à cocher pour spécifier une valeur par défaut.  
  
 Entrez une valeur par défaut. Il peut s'agir d'une valeur statique ou d'une expression qui fait référence à un objet dans le rapport. L'expression ne peut pas faire référence aux éléments de rapport, aux paramètres de rapport ni aux champs.  
  
 Pour spécifier une valeur vide, laissez la zone de texte vide.  
  
 Pour spécifier une valeur Null, sélectionnez l'option Nullable.  
  
 **Lecture seule**  
 Pour les datasets partagés uniquement.  
  
 Sélectionnez cette option pour marquer ce paramètre comme étant en lecture seule dans la définition de dataset partagé. Lorsque le dataset partagé est ajouté à un rapport, le paramètre ne s'affiche pas dans les propriétés. Lorsque le dataset partagé est mis en cache sur le serveur de rapports, la valeur ne peut pas être modifiée.  
  
 **Nullable**  
 Pour les datasets partagés uniquement.  
  
 Sélectionnez cette option pour autoriser une valeur Null.  
  
 **Omettre de la requête**  
 Pour les datasets partagés uniquement.  
  
 Sélectionnez cette option lorsqu'une référence à un paramètre de rapport figure dans une expression dans le filtre de dataset partagé et pas dans la requête. Lorsque vous sélectionnez cette option, vous n'avez pas besoin de spécifier une valeur par défaut pour ce paramètre lors de l'exécution de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Boîte de dialogue Propriétés de DataSet, requête &#40;Générateur de rapports&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Didacticiel : Ajouter un paramètre à votre rapport &#40;Générateur de rapports&#41;](tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../../2014/reporting-services/query-designers-report-builder.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
  
