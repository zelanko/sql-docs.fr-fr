---
title: Conversion de schémas DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7947efc3-ca86-4ec5-87ce-7603059c75a0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7a16a28a163acece321cc2229e9988cf7ab01f9e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989866"
---
# <a name="converting-db2-schemas-db2tosql"></a>Conversion de schémas DB2 (DB2ToSQL)
Après vous être connecté à DB2, connecté à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et définir le projet et les options de mappage de données, vous pouvez convertir des objets de base de données DB2 à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets de base de données.  
  
## <a name="the-conversion-process"></a>Le processus de Conversion  
Convertir des objets de base de données accepte les définitions d’objets à partir de DB2, les convertit en similaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets et charge ensuite ces informations dans les métadonnées SSMA. Il ne charge pas les informations dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez ensuite afficher les objets et leurs propriétés à l’aide de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées.  
  
Lors de la conversion, SSMA imprime les messages de sortie dans le volet de sortie et messages d’erreur vers le volet Liste d’erreurs. Utilisez les informations de sortie et d’erreur pour déterminer si vous devez modifier vos bases de données DB2 ou votre processus de conversion pour obtenir les résultats de la conversion souhaitée.  
  
## <a name="setting-conversion-options"></a>Définition des Options de Conversion  
Avant de convertir des objets, passez en revue les options de conversion de projet dans le **paramètres du projet** boîte de dialogue. À l’aide de cette boîte de dialogue, vous pouvez définir comment SSMA convertit les fonctions et variables globales. Pour plus d’informations, consultez [paramètres du projet &#40;Conversion&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
## <a name="conversion-results"></a>Résultats de la conversion  
Le tableau suivant présente les objets de DB2 sont convertis et résultant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets :  
  
|Objets de DB2|Objets SQL Server qui en résulte|  
|-----------|----------------------------|  
|Types de données|**SSMA mappe chaque type à l’exception des éléments répertoriés ci-dessous :**<br /><br />CLOB : Certaines des fonctions natives pour travailler avec ce type ne sont pas pris en charge (par exemple, CLOB_EMPTY())<br /><br />OBJET BLOB : Certaines des fonctions natives pour travailler avec ce type ne sont pas pris en charge (par exemple, BLOB_EMPTY())<br /><br />DBLOB : Certaines des fonctions natives pour travailler avec ce type ne sont pas pris en charge (par exemple, DBLOB_EMPTY())|  
|Types définis par l'utilisateur|**SSMA mappe les éléments suivants définis par l’utilisateur :**<br /><br />Type distinct<br /><br />Type structuré<br /><br />Types de données SQL PL - Remarque : Type de curseur faible ne sont pas pris en charge.|  
|Registres spéciaux|**SSMA mappe uniquement les registres répertoriés ci-dessous :**<br /><br />HORODATEUR ACTUEL<br /><br />DATE ACTUELLE<br /><br />HEURE ACTUELLE<br /><br />FUSEAU HORAIRE ACTUEL<br /><br />UTILISATEUR ACTUEL<br /><br />SESSION_USER et utilisateur<br /><br />SYSTEM_USER<br /><br />CLIENT_APPLNAME ACTUEL<br /><br />CLIENT_WRKSTNNAME ACTUEL<br /><br />DÉLAI D’ATTENTE DE VERROU ACTUEL<br /><br />SCHÉMA ACTUEL<br /><br />SERVEUR ACTUEL<br /><br />ISOLATION ACTUELLE<br /><br />Autres registres spéciaux ne sont pas mappés à la sémantique de SQL server.|  
|CREATE TABLE|**SSMA est mappé à créer une TABLE avec les exceptions suivantes :**<br /><br />Tables de clustering (MDC) multidimensionnel<br /><br />Tables de plage en cluster (RCT)<br /><br />tables partitionnées ;<br /><br />Table détaché<br /><br />Clause de CAPTURE de données<br /><br />Option IMPLICITLY masqué<br /><br />Option VOLATILE|  
|CREATE VIEW|SSMA est mappé à créer un affichage avec 'WITH LOCAL CHECK OPTION' mais d’autres options ne sont pas mappées à la sémantique SQL server|  
|CREATE INDEX|**SSMA mappe CREATE INDEX avec les exceptions suivantes :**<br /><br />Index XML<br /><br />Option BUSINESS_TIME sans chevauchement<br /><br />Clause partitionnée<br /><br />Option de spécification uniquement<br /><br />Option à l’aide de l’extension<br /><br />Option de MINPCTUSED<br /><br />Option de fractionnement de PAGE|  
|Déclencheurs|**SSMA est mappé à la sémantique de déclencheur suivante :**<br /><br />Une fois / pour les déclencheurs de chaque ligne<br /><br />Après avoir /FOR chaque instruction déclenche<br /><br />AVANT / pour chaque ligne et au lieu de / pour les déclencheurs de chaque ligne|  
|Séquences|Sont mappées.|  
|Instruction SELECT|**Mappages SSMA sélectionnez avec les exceptions suivantes :**<br /><br />Clause de données-modification-table-reference - partiellement mappé, mais les tables finales ne non pris en charge<br /><br />Clause de référence de table - partiellement mappé, mais uniquement--référence de table, référence de table externe, analyze_table-expression, table collection dérivée, xmltable-expression ne sont pas mappés à la sémantique SQL server<br /><br />Clause de spécification de la période - ne pas mappée.<br /><br />Clause de gestionnaire Continuer - ne pas mappée.<br /><br />Clause de corrélation tapé - ne pas mappée.<br /><br />Clause de résolution de l’accès simultané - ne pas mappée.|  
|Instruction de valeurs|Est mappée.|  
|Instruction INSERT|Est mappée.|  
|Instruction de mise à jour|S**SMA mappe la mise à jour avec les exceptions suivantes :**<br /><br />Clause de référence de table-uniquement--référence de table n’est pas mappé à la sémantique SQL server<br /><br />Clause période - n’est pas mappé.|  
|Instruction MERGE|**SSMA mappe la fusion avec les exceptions suivantes :**<br /><br />Une seule / plusieurs Occurrences de chaque Clause - est mappé à la sémantique SQL server limité occurrences de chaque clause<br /><br />Clause SIGNAL - ne mappe pas à la sémantique de SQL Server<br /><br />Mixte mise à jour et supprimer des Clauses - ne mappe pas à la sémantique de SQL Server<br /><br />Clause de période - ne mappe pas à la sémantique de SQL Server|  
|DELETE, instruction|**SUPPRIMER des mappages SSMA avec les exceptions suivantes :**<br /><br />Clause de référence de table-uniquement--référence de table n’est pas mappé à la sémantique SQL server<br /><br />Clause période - ne mappe pas à la sémantique de SQL Server|  
|Niveau d’isolement et le Type de verrou|Est mappée.|  
|Procédures (SQL)|Sont mappées.|  
|Procédures (externe)|Nécessitent la mise à jour manuelle.|  
|Procédures (source)|Ne correspondent pas à la sémantique de SQL Server.|  
|Instruction d’assignation|Est mappée.|  
|Instruction d’appel pour une procédure|Est mappée.|  
|Instruction CASE|Est mappée.|  
|Instruction FOR|Est mappée.|  
|GOTO (instruction)|Est mappée.|  
|Instruction IF|Est mappée.|  
|Effectuer une itération d’instruction|Est mappée.|  
|Laissez l’instruction|Est mappée.|  
|Instruction de boucle|Est mappée.|  
|RÉPÉTEZ l’instruction|Est mappée.|  
|SIGNALER l’instruction|Conditions ne sont pas prises en charge. Les messages peuvent être facultatifs.|  
|RETURN (instruction)|Est mappée.|  
|Instruction de SIGNAL|Conditions ne sont pas prises en charge. Les messages peuvent être facultatifs.|  
|WHILE, instruction|Est mappée.|  
|GET (instruction) DIAGNOSTICS|**SSMA est mappé à obtenir des DIAGNOSTICS avec les exceptions suivantes :**<br /><br />ROW_COUNT - est mappé.<br /><br />DB2_RETURN_STATUS - est mappé.<br /><br />MESSAGE_TEXT - est mappé.<br /><br />DB2_SQL_NESTING_LEVEL - ne mappe pas à la sémantique de SQL Server<br /><br />DB2_TOKEN_STRING - ne mappe pas à la sémantique de SQL Server|  
|Curseurs|**SSMA mappe les curseurs avec les exceptions suivantes :**<br /><br />Instruction de curseur de l’allocation - ne mappe pas à la sémantique de SQL Server<br /><br />Instruction d’associer les LOCALISATEURS - ne mappe pas à la sémantique de SQL Server<br /><br />Instruction DECLARE CURSOR - clause de Returnability n’est pas mappée à la sémantique SQL server<br /><br />Instruction FETCH - mappage partiel. Variables en tant que cible sont uniquement pris en charge. DESCRIPTEUR SQLDA n’est pas mappé à la sémantique SQL server|  
|Variables|Sont mappées.|  
|Exceptions, les gestionnaires et les Conditions|**SSMA est mappé à « exceptions » avec les exceptions suivantes :**<br /><br />Gestionnaires de sortie - sont mappées.<br /><br />Annuler les gestionnaires - sont mappées.<br /><br />Gestionnaires de continuer, ne sont pas mappés.<br /><br />Conditions - elle ne mappe pas à la sémantique SQL server.|  
|SQL dynamique|Non mappé.|  
|Alias|Sont mappées.|  
|Surnoms|Mappage partiel. Traitement manuel est nécessaire pour l’objet sous-jacent|  
|Synonymes|Sont mappées.|  
|Fonctions standard dans DB2|SSMA mappe des fonctions standards DB2 lorsqu’une fonction équivalente est disponible dans SQL Server :|  
|Authorization|Non mappé.|  
|Prédicats|Sont mappées.|  
|SELECT INTO, instruction|Non mappé.|  
|Les valeurs dans l’instruction|Non mappé.|  
|Contrôle des transactions|Non mappé.|  
  
## <a name="converting-db2-database-objects"></a>Convertir des objets de base de données DB2  
Pour convertir des objets de base de données DB2, vous sélectionnez d’abord les objets que vous souhaitez convertir, puis SSMA effectuer la conversion. Pour afficher les messages de sortie pendant la conversion, sur le **vue** menu, sélectionnez **sortie**.  
  
**Pour convertir des objets DB2 en syntaxe de SQL Server**  
  
1.  Dans l’Explorateur de métadonnées de DB2, développez le serveur DB2, puis puis **schémas**.  
  
2.  Sélectionnez les objets à convertir :  
  
    -   Pour convertir tous les schémas, sélectionnez la case à cocher à côté **schémas**.  
  
    -   Pour convertir ou omettre une base de données, sélectionnez la case à cocher en regard du nom de schéma.  
  
    -   Pour convertir ou omettre une catégorie d’objets, développez un schéma, puis sélectionnez ou désactivez la case à cocher en regard de la catégorie.  
  
    -   Pour convertir ou omettre des objets, développez le dossier de catégorie, puis sélectionnez ou désactivez la case à cocher en regard de l’objet.  
  
3.  Pour convertir tous les objets sélectionnés, cliquez sur **schémas** et sélectionnez **convertir le schéma**.  
  
    Vous pouvez également convertir des objets individuels ou des catégories d’objets en double-cliquant sur l’objet ou son dossier parent, puis en sélectionnant **convertir le schéma**.  
  
## <a name="viewing-conversion-problems"></a>Affichage des problèmes de Conversion  
Certains objets DB2 ne peuvent pas être converties. Vous pouvez déterminer le taux de réussite de la conversion en affichant le rapport de synthèse de conversion.  
  
**Pour afficher un rapport de synthèse**  
  
1.  Dans l’Explorateur de métadonnées de DB2, sélectionnez **schémas**.  
  
2.  Dans le volet droit, sélectionnez le **rapport** onglet.  
  
    Ce rapport affiche le rapport d’évaluation de résumé pour tous les objets de base de données qui ont été évaluées ou converti. Vous pouvez également afficher un rapport de synthèse pour des objets individuels :  
  
    -   Pour afficher le rapport pour un schéma individuel, sélectionnez le schéma dans l’Explorateur de métadonnées DB2.  
  
    -   Pour afficher le rapport pour un objet individuel, sélectionnez l’objet dans l’Explorateur de métadonnées DB2. Les objets qui présentent des problèmes de conversion ont une icône d’erreur rouge.  
  
Pour les objets en échec de conversion, vous pouvez afficher la syntaxe qui a entraîné l’échec de conversion.  
  
**Pour afficher les problèmes de conversion individuels**  
  
1.  Dans l’Explorateur de métadonnées de DB2, développez **schémas**.  
  
2.  Développez le schéma qui affiche une icône d’erreur rouge.  
  
3.  Sous le schéma, développez un dossier qui a une icône d’erreur rouge.  
  
4.  Sélectionnez l’objet qui a une icône d’erreur rouge.  
  
5.  Dans le volet droit, cliquez sur le **rapport** onglet.  
  
6.  En haut de la **rapport** onglet est une liste déroulante. Si la liste affiche **statistiques**, modifiez la sélection à **Source**.  
  
    SSMA affichera le code source et plusieurs boutons immédiatement au-dessus du code.  
  
7.  Cliquez sur le **problème suivant** bouton. Il s’agit d’une icône d’erreur rouge avec une flèche qui pointe vers la droite.  
  
    SSMA met en évidence le premier code source problématiques qu’il trouve dans l’objet actuel.  
  
Pour chaque élément qui ne peut pas être converti, vous devez déterminer ce que vous voulez faire avec cet objet :  
  
-   Vous pouvez modifier le code source pour les procédures sur le **SQL** onglet.  
  
-   Vous pouvez modifier l’objet dans la base de données DB2 pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devrez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à la base de données DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
-   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées et l’Explorateur de métadonnées de DB2, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migration des données à partir de DB2.  
  
## <a name="next-step"></a>Étape suivante  
L’étape suivante du processus de migration consiste à [charger les objets convertis dans SQL Server](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3).  
  
## <a name="see-also"></a>Voir aussi  
[Migration de données DB2 dans SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
