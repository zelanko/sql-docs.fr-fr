---
title: Paramètres du projet (migration) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration settings
- Project Settings dialog box, Migration
ms.assetid: 4caebc9c-8680-4b99-a8fa-89c43161c95d
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3e3d979b6f3c5943723fb5dd8f37831adfbc1305
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67929396"
---
# <a name="project-settings-migration-accesstosql"></a>Paramètres du projet (migration) (AccessToSQL)
Les paramètres du projet de migration vous permettent de configurer la façon dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les données sont migrées vers ou SQL Azure.  
  
Le volet migration est disponible dans les boîtes de dialogue **paramètres du projet** et **paramètres du projet par défaut** .  
  
-   Utilisez la boîte de dialogue **paramètres du projet** pour définir les options de configuration du projet actif. Pour accéder aux paramètres de migration, dans le menu **Outils** , sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **migration**.  
  
-   Utilisez la boîte de dialogue **paramètres du projet par défaut** pour définir les options de configuration de tous les projets. Pour accéder aux paramètres de migration, dans le menu **Outils** , sélectionnez **paramètres du projet par défaut**, sélectionnez le type de projet dans la zone de liste déroulante cible de la **migration** dont vous souhaitez accéder aux paramètres, cliquez sur **général** en bas du volet gauche, puis cliquez sur **migration**.  
  
## <a name="options"></a>Options  
**Contraintes de validation**  
Spécifie si SSMA doit vérifier les contraintes lorsqu’il ajoute des données aux tables.  
  
-   **Mode par défaut**: false  
  
-   **Mode optimiste**: true  
  
-   **Mode complet**: false  
  
**Déclencher les déclencheurs**  
Spécifie si SSMA doit déclencher les déclencheurs d’insertion lorsqu’il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ajoute des données aux tables.  
  
-   **Mode par défaut**: false  
  
-   **Mode optimiste**: true  
  
-   **Mode complet**: false  
  
**Conserver l’identité**  
Spécifie si SSMA conserve les valeurs d’identité d’accès lorsqu’il ajoute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données à. Si cette valeur est false [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , assigne des valeurs d’identité.  
  
-   **Mode par défaut**: true  
  
-   **Mode optimiste**: true  
  
-   **Mode complet**: false  
  
**Conserver les valeurs null**  
Spécifie si SSMA conserve les valeurs NULL dans les données sources lorsqu’il ajoute des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à, quelles que soient les valeurs par défaut spécifiées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Mode par défaut**: true  
  
-   **Mode optimiste**: false  
  
-   **Mode complet**: true  
  
**Verrous de table**  
Spécifie si SSMA verrouille des tables lorsqu’il ajoute des données aux tables pendant la migration des données. Si la valeur est false, SSMA utilise des verrous de ligne.  
  
-   **Mode par défaut**: true  
  
-   **Mode optimiste**: true  
  
-   **Mode complet**: true  
  
**Remplacer les dates non prises en charge**  
Spécifie si SSMA doit corriger les dates d’accès antérieures à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date du DateTime la plus ancienne (01 janvier 1753).  
  
-   Pour conserver les valeurs de date actuelles, sélectionnez **ne rien faire**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]n’accepte pas les dates antérieures au 1er janvier 1753 dans une colonne DateTime. Si vous utilisez des dates antérieures, vous devez convertir les valeurs DateTime en valeurs de caractères.  
  
-   Pour convertir les dates antérieures au 1er janvier 1753 en NULL, sélectionnez **remplacer par null**.  
  
-   Pour remplacer les dates antérieures au 1er janvier 1753 par une Date prise en charge, sélectionnez **remplacer par la date de prise en charge la plus proche**. Si vous sélectionnez cette valeur, par défaut, la date de prise en charge la plus proche sera sélectionnée en tant que 01 janvier 1753.  
  
**Taille du lot**  
Taille de lot utilisée lors de la migration des données. Une transaction est journalisée après chaque lot. Par défaut, la taille de lot pour tous les schémas est 10000.  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’interface utilisateur (accès)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
