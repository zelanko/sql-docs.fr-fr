---
title: Analyser dans Excel (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2f17b4df-eea2-48c7-a1f2-a3fb7748c15f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f8090c75108f7a384019030082699917fca915b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067687"
---
# <a name="analyze-in-excel-ssas-tabular"></a>Analyser dans Excel (SSAS Tabulaire)
  La fonctionnalité Analyser dans Excel de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]offre aux créateurs de modèles tabulaires un moyen d'analyser rapidement les projets de modèle au cours du développement. La fonctionnalité Analyser dans Excel ouvre l'application Microsoft Excel, crée une connexion de source de données à la base de données model de l'espace de travail, puis ajoute automatiquement un tableau croisé dynamique à la feuille de calcul. Les objets de base de données de l'espace de travail (tables, colonnes et mesures) sont inclus en tant que champs dans la liste de champs du tableau croisé dynamique. Les objets et les données peuvent ensuite être affichés dans le contexte du rôle ou de l'utilisateur effectif et de la perspective.  
  
 Cette rubrique part du principe que vous êtes familiarisé avec Microsoft Excel et savez déjà utiliser des tableaux croisés dynamiques et des graphiques croisés dynamiques. Pour en savoir plus sur l'utilisation d'Excel, consultez l'aide relative à cette application.  
  
 Sections de cette rubrique :  
  
-   [Avantages](#bkmk_benefits)  
  
-   [Tâches associées](#bkmk_rt)  
  
##  <a name="bkmk_benefits"></a>Avantageuse  
 La fonctionnalité Analyser dans Excel permet aux créateurs de modèles de tester l'efficacité d'un projet de modèle à l'aide de l'application courante d'analyse de données, Microsoft Excel. Pour utiliser la fonctionnalité Analyser dans Excel, vous devez disposer de Microsoft Office 2003 ou d'une version ultérieure installée sur le même ordinateur que [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Si Office n'est pas installé sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez utiliser Excel sur un autre ordinateur pour vous connecter à la base de données de l'espace de travail en tant que source de données. Vous pouvez ensuite ajouter manuellement un tableau croisé dynamique à la feuille de calcul.  
  
 La fonctionnalité Analyser dans Excel ouvre Excel et crée un nouveau classeur Excel (.xls). Une connexion de données du classeur à la base de données model de l'espace de travail est créée. Un tableau croisé dynamique vide est ajouté à la feuille de calcul et des métadonnées d'objet de modèle alimentent la liste de champs de tableau croisé dynamique. Vous pouvez ajouter des données visibles et des segments au tableau croisé dynamique.  
  
 Lors de l'utilisation de la fonctionnalité Analyser dans Excel, par défaut, le compte d'utilisateur actuellement connecté correspond à l'utilisateur effectif. Ce compte est généralement un administrateur sans restrictions d'affichage sur les objets de modèle ou les données. Vous pouvez toutefois spécifier un rôle ou un nom d'utilisateur effectif différent. Cela vous permet d'explorer un projet de modèle dans Excel dans le contexte d'un utilisateur ou d'un rôle spécifique. La spécification de l'utilisateur effectif inclut les options suivantes :  
  
 **Utilisateur Windows actuel**  
 Utilise le compte d'utilisateur avec lequel vous êtes connecté.  
  
 **Autre utilisateur Windows**  
 Utilise un nom d'utilisateur Windows spécifié au lieu de l'utilisateur actuellement connecté. L'utilisation d'un autre utilisateur Windows ne requiert pas de mot de passe. Les objets et les données ne peuvent être affichés dans Excel que dans le contexte du nom d'utilisateur effectif. Aucune modification aux objets de modèle ou aux données ne peut être effectuée dans Excel.  
  
 **Actif**  
 Un rôle est utilisé pour définir les autorisations utilisateur sur les métadonnées et les données d'objets. Les rôles sont généralement définis pour un utilisateur ou un groupe d'utilisateurs Windows particulier. Certains rôles peuvent inclure des filtres supplémentaires au niveau de la ligne définis dans une formule DAX. Lors de l'utilisation de la fonctionnalité Analyser dans Excel, vous pouvez éventuellement sélectionner un rôle à utiliser. Les métadonnées et les vues de données d'objet sont limitées par l'autorisation et les filtres définis pour le rôle. Pour plus d’informations, consultez [Créer et gérer des rôles &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md).  
  
 En plus du rôle ou de l'utilisateur effectif, vous pouvez spécifier une perspective. Les perspectives permettent aux créateurs de modèles de définir des vues particulières de scénario d'entreprise des objets de modèle et des données. Par défaut, aucune perspective n'est utilisée. Pour utiliser une perspective avec la fonctionnalité Analyser dans Excel, il faut que des perspectives soient déjà définies à l'aide de la boîte de dialogue Perspectives de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Si une perspective est spécifiée, la liste de champs de tableau croisé dynamique contient uniquement les objets sélectionnés dans la perspective. Pour plus d’informations, consultez [créer et gérer des Perspectives &#40;&#41;tabulaires SSAS ](perspectives-ssas-tabular.md).  
  
##  <a name="bkmk_rt"></a> Tâches associées  
  
|**Rubrique**|**Description**|  
|---------------|---------------------|  
|[Analyser un modèle tabulaire dans Excel &#40;la&#41;tabulaire SSAS](analyze-a-tabular-model-in-excel-ssas-tabular.md)|Cette rubrique décrit comment utiliser la fonctionnalité Analyser dans Excel dans le concepteur de modèles afin d'ouvrir Excel, créer une connexion de source de données à la base de données model de l'espace de travail et ajouter un tableau croisé dynamique à la feuille de calcul.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser un modèle tabulaire dans Excel &#40;la&#41;tabulaire SSAS](analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [Rôles &#40;&#41;tabulaire SSAS](roles-ssas-tabular.md)   
 [Perspectives &#40;&#41;tabulaire SSAS](perspectives-ssas-tabular.md)  
  
  
