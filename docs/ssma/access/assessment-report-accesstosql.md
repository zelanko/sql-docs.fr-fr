---
description: Rapport d’évaluation (AccessToSQL)
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6c747f50c9216626e710318175cf5e53a0624d7a
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987655"
---
# <a name="assessment-report-accesstosql"></a>Rapport d’évaluation (AccessToSQL)
La fenêtre rapport d’évaluation affiche les résultats de la conversion des objets de base de données en [!INCLUDE[tsql](../../includes/tsql-md.md)] syntaxe et peut également vous aider à estimer la complexité et le coût de vos projets de migration.  
  
Pour créer un rapport d’évaluation, sélectionnez les objets à convertir dans l’Explorateur de métadonnées source, cliquez avec le bouton droit sur **bases de données**, puis sélectionnez **créer un rapport**. Vous pouvez également afficher ce rapport automatiquement après la conversion de schémas. Toutefois, le nom du rapport sera un rapport de conversion. Pour plus d’informations, consultez [paramètres du projet (GUI) (SSMA commun)](../sybase/project-settings-gui-sybasetosql.md).  
  
## <a name="options"></a>Options  
**Volet Explorateur**  
Contient une hiérarchie d’objets dans le rapport d’évaluation. Développez les dossiers pour afficher des objets et des sous-composants individuels. Lorsque vous cliquez sur une catégorie ou un objet, les statistiques de conversion de cette catégorie ou de cet objet s’affichent dans le volet d’informations.  
  
**Volet d’informations**  
Affiche les statistiques de conversion ou les messages d’erreur et d’avertissement pour l’objet sélectionné. Par exemple, si le dossier tables est sélectionné, le volet Détails affiche le nombre de clés étrangères, d’index, de clés primaires et de tables qui ont été convertis.  
  
**Volet Messages**  
Affiche les erreurs, avertissements et messages d’information qui ont été générés lors de la création du rapport d’évaluation. Les messages sont regroupés par nombre.  
  
Pour afficher les détails d’un message, cliquez sur **Erreurs**, **avertissements**ou **messages**, puis développez un message. SSMA affiche la liste des objets qui ont cette erreur. Cliquez sur un objet pour afficher tous les détails de la conversion de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’interface utilisateur (accès)](./user-interface-reference-accesstosql.md)  
