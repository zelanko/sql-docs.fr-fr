---
title: xp_logininfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c9ed0ee742d1562d8b573b71e5d62b7d10bc7d02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843827"
---
# <a name="xplogininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les utilisateurs Windows et les groupes Windows.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@acctname =** ] **'***account_name***'**  
 Nom d'un utilisateur ou groupe Windows autorisé à accéder à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *nom_compte* est **sysname**, avec NULL comme valeur par défaut. Si *account_name* n’est pas spécifié, tous les groupes de Windows et les utilisateurs Windows qui ont été explicitement accordé l’autorisation de se connecter sont signalés. *nom_compte* doivent être qualifiés complets. Par exemple, « ADVWKS4\macraes » ou « BUILTIN\Administrators ».  
  
 **'all'** | **« members »**  
 Spécifie s'il faut rapporter les informations sur tous les chemins d'autorisation du compte ou sur les membres du groupe Windows. **@option** est **varchar (10)**, avec NULL comme valeur par défaut. À moins que **tous les** est spécifié, seul le chemin de la première autorisation s’affiche.  
  
 [  **@privilege =** ] *nom_variable*  
 Paramètre de sortie qui retourne le niveau de privilège du compte Windows spécifié. *nom_variable* est **varchar (10)**, avec une valeur par défaut « Not wanted ». Le niveau de privilège renvoyé est **utilisateur**, **administrateur**, ou **null**.  
  
 OUTPUT  
 Lorsqu’elle est spécifiée, place *nom_variable* dans le paramètre de sortie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Nom du compte**|**sysname**|Nom de compte Windows complet.|  
|**type**|**char (8)**|Type de compte Windows. Les valeurs valides sont **utilisateur** ou **groupe**.|  
|**privilège**|**char(9)**|Privilège d'accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les valeurs valides sont **administrateur**, **utilisateur**, ou **null**.|  
|**nom de connexion mappé**|**sysname**|Comptes d’utilisateurs avec privilège utilisateur, **mappé le nom de connexion** affiche le nom de connexion mappée qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente d’utiliser lors de l’ajout de journalisation avec ce compte en utilisant les règles de mappage avec le nom de domaine avant qu’elle.|  
|**chemin d’accès de l’autorisation**|**sysname**|Membre du groupe qui autorise l'accès au compte|  
  
## <a name="remarks"></a>Notes  
 Si *account_name* est spécifié, **xp_logininfo** indique le niveau de privilège le plus élevé de l’utilisateur Windows spécifié ou le groupe. Si un utilisateur Windows dispose d'autorisations d'accès en tant qu'administrateur système et utilisateur de domaine, il est indiqué comme administrateur système. Si l'utilisateur est membre de plusieurs groupes Windows dotés des mêmes niveaux de privilèges, seul le groupe qui a obtenu le premier l'accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est indiqué.  
  
 Si *account_name* est un utilisateur de Windows valide ou un groupe qui n’est pas associé à une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, le jeu de résultats vide est retourné. Si *account_name* ne peut pas être identifié comme un utilisateur Windows valide ou un groupe, un message d’erreur est retourné.  
  
 Si *account_name* et **tous les** sont spécifiés, tous les chemins d’autorisation pour l’utilisateur de Windows ou d’un groupe sont retournés. Si *account_name* est un membre de plusieurs groupes, qui ont tous été autorisation d’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], plusieurs lignes sont retournées. Le **administrateur** lignes avec le privilège sont retournées avant le **utilisateur** privilèges des lignes et au sein d’un privilège au niveau lignes sont retournées dans l’ordre dans lequel correspondant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexions ont été créées.  
  
 Si *account_name* et **membres** sont spécifiés, une liste des membres du groupe de niveau suivant est retournée. Si *account_name* est un groupe local, la liste peut inclure des utilisateurs, les utilisateurs de domaine et groupes locaux. Si *account_name* est un compte de domaine, la liste est composée d’utilisateurs de domaine. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit se connecter au contrôleur de domaine pour extraire les informations d'appartenance au groupe. Si le serveur ne peut pas contacter le contrôleur de domaine, aucune information n'est renvoyée.  
  
 **xp_logininfo** retourne uniquement des informations à partir de groupes globaux Active Directory, les groupes universels pas.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance au **sysadmin** rôle serveur fixe ou l’appartenance à la **public** rôle de base de données fixe dans le **master** base de données avec l’autorisation EXECUTE accordée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant affiche des informations sur la `BUILTIN\Administrators` groupe de Windows.  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées étendues générales &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
