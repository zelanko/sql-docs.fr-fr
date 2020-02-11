---
title: Rapport d’évaluation (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Assessment Report dialog box
- Conversion Report dialog box
ms.assetid: ba6f53aa-0049-4c49-8bb8-607a8bfaa737
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c28fb4cf5d110e01b156fc6ce985b2cb2fb7bfe1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910686"
---
# <a name="assessment-report-accesstosql"></a>Rapport d’évaluation (AccessToSQL)
La fenêtre rapport d’évaluation affiche les résultats de la conversion des objets de [!INCLUDE[tsql](../../includes/tsql-md.md)] base de données en syntaxe et peut également vous aider à estimer la complexité et le coût de vos projets de migration.  
  
Pour créer un rapport d’évaluation, sélectionnez les objets à convertir dans l’Explorateur de métadonnées source, cliquez avec le bouton droit sur **bases de données**, puis sélectionnez **créer un rapport**. Vous pouvez également afficher ce rapport automatiquement après la conversion de schémas. Toutefois, le nom du rapport sera un rapport de conversion. Pour plus d’informations, consultez [paramètres du projet (GUI) (SSMA commun)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
## <a name="options"></a>Options  
**Volet Explorateur**  
Contient une hiérarchie d’objets dans le rapport d’évaluation. Développez les dossiers pour afficher des objets et des sous-composants individuels. Lorsque vous cliquez sur une catégorie ou un objet, les statistiques de conversion de cette catégorie ou de cet objet s’affichent dans le volet d’informations.  
  
**Volet d’informations**  
Affiche les statistiques de conversion ou les messages d’erreur et d’avertissement pour l’objet sélectionné. Par exemple, si le dossier tables est sélectionné, le volet Détails affiche le nombre de clés étrangères, d’index, de clés primaires et de tables qui ont été convertis.  
  
**Volet Messages**  
Affiche les erreurs, avertissements et messages d’information qui ont été générés lors de la création du rapport d’évaluation. Les messages sont regroupés par nombre.  
  
Pour afficher les détails d’un message, cliquez sur **Erreurs**, **avertissements**ou **messages**, puis développez un message. SSMA affiche la liste des objets qui ont cette erreur. Cliquez sur un objet pour afficher tous les détails de la conversion de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’interface utilisateur (accès)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
