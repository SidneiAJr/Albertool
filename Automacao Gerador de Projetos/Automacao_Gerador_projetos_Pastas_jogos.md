# 🎮 Automação | Criação Rápida de Estrutura de Jogos

## 🛠️ Script de Automação – Unity C# & Godot C#

## ⚙️ O que você encontra aqui?

Este script automatiza a criação de um projeto base para jogos usando:

- Unity (C#)

- Godot (C#)

- Unreal(C++)

## `O objetivo é agilizar o início de qualquer jogo, criando`:

###  `📁 Estrtura de Pastas| Unity` : 

```bash
 Assets/
📁 Unity/
├── 📁 Scripts/
│  ├── PlayerMovement.cs
│  ├── PlayerStatus.cs
│  ├── EnemyAI.cs
│  ├── DropItems.cs
│  ├── Gate.cs
│  ├── Teleport.cs
│  ├── Weapon.cs
│  ├── MenuInicial.cs
│  ├── MenuFinal.cs
│  └── CGI.cs
│
├── 📁 Prefabs/
├── 📁 Scenes/
├── 📁 Animations/
├── 📁 UI/
├── 📁 Player/
├── 📁 Enemies/
├── 📁 Items/
├── 📁 Weapons/
├── 📁 Environment/
├── 📁 Systems/
├── 📁 TMP/
├── 📁 SceneManager/
├── 📁 Animator/
│
└── 📁 Documentation/
   ├── README.md
   ├── Architecture.md
   ├── Controls.md
   └── Roadmap.md

```

## Script Abaixo 

- Rodar em com .sh

````bash
#!/bin/bash

echo "🎮 Bem-vindo ao Criador de Projetos GameDev"
echo "Escolha a Engine:"
echo "1) Unity"
echo "2) Godot C#"
echo "3) Unreal C++"
read -p "Digite o número: " engine

# ============================================
# FUNÇÃO PARA CRIAR DOCUMENTAÇÃO PADRÃO
# ============================================
create_docs() {
    local path=$1

    mkdir -p "$path/Documentation"

    echo "# 📘 Documentação do Projeto" > "$path/Documentation/README.md"
    echo "Este projeto foi gerado automaticamente pelo GameDev Project Generator." >> "$path/Documentation/README.md"
    echo "" >> "$path/Documentation/README.md"
    echo "## Estrutura" >> "$path/Documentation/README.md"
    echo "- Scripts" >> "$path/Documentation/README.md"
    echo "- Scenes" >> "$path/Documentation/README.md"
    echo "- Systems" >> "$path/Documentation/README.md"

    echo "# Arquitetura" > "$path/Documentation/Architecture.md"
    echo "Documentação futura da arquitetura do projeto." >> "$path/Documentation/Architecture.md"

    echo "# Controles" > "$path/Documentation/Controls.md"
    echo "Escreva aqui os controles do jogador." >> "$path/Documentation/Controls.md"

    echo "# Roadmap" > "$path/Documentation/Roadmap.md"
    echo "- [ ] Implementar gameplay básico" >> "$path/Documentation/Roadmap.md"
    echo "- [ ] Criar UI" >> "$path/Documentation/Roadmap.md"
    echo "- [ ] Adicionar sistemas" >> "$path/Documentation/Roadmap.md"
}

# ============================================
# -------------- UNITY ------------------------
# ============================================
if [ "$engine" = "1" ]; then
    echo "🛠 Criando estrutura Unity..."

    base="Unity"
    mkdir -p $base/{Scripts,Prefabs,Scenes,Animations,UI,Player,Enemies,Items,Weapons,Environment,Systems,TMP,SceneManager,Animator}

    create_docs "$base"

    files=(
        "PlayerMovement.cs"
        "PlayerStatus.cs"
        "EnemyAI.cs"
        "DropItems.cs"
        "Gate.cs"
        "Teleport.cs"
        "Weapon.cs"
        "MenuInicial.cs"
        "MenuFinal.cs"
        "CGI.cs"
    )

    for file in "${files[@]}"; do
        path="$base/Scripts/$file"
        echo "// $file - Script gerado automaticamente" > $path
        echo "using UnityEngine;" >> $path
        echo "" >> $path
        echo "public class ${file%.*} : MonoBehaviour {" >> $path
        echo "    void Start() {}" >> $path
        echo "    void Update() {}" >> $path
        echo "}" >> $path
    done

    echo "✅ Unity pronta!"
fi

# ============================================
# -------------- GODOT C# ---------------------
# ============================================
if [ "$engine" = "2" ]; then
    echo "🛠 Criando estrutura Godot..."

    base="Godot"
    mkdir -p $base/{Scripts,Scenes,UI,Player,Enemies,Items,Weapons,Environment,Systems,SceneManager,Animator}

    create_docs "$base"

    files=(
        "PlayerMovement.cs"
        "PlayerStatus.cs"
        "EnemyAI.cs"
        "DropItems.cs"
        "Gate.cs"
        "Teleport.cs"
        "Weapon.cs"
        "MenuInicial.cs"
        "MenuFinal.cs"
        "CGI.cs"
    )

    for file in "${files[@]}"; do
        path="$base/Scripts/$file"
        echo "// $file - Script gerado automaticamente" > $path
        echo "using Godot;" >> $path
        echo "" >> $path
        echo "public partial class ${file%.*} : Node {" >> $path
        echo "    public override void _Ready() {}" >> $path
        echo "    public override void _Process(double delta) {}" >> $path
        echo "}" >> $path
    done

    echo "✅ Godot pronta!"
fi

# ============================================
# -------------- UNREAL C++ -------------------
# ============================================
if [ "$engine" = "3" ]; then
    echo "🛠 Criando estrutura Unreal..."

    base="Unreal"
    mkdir -p $base/{Source,Header,Player,Enemies,Items,Weapons,Environment,Systems,SceneManager,Animator}

    create_docs "$base"

    files=(
        "PlayerMovement"
        "PlayerStatus"
        "EnemyAI"
        "DropItems"
        "Gate"
        "Teleport"
        "Weapon"
        "MenuInicial"
        "MenuFinal"
        "CGI"
    )

    for name in "${files[@]}"; do
        hfile="$base/Header/${name}.h"
        cppfile="$base/Source/${name}.cpp"

        # HEADER
        echo "// ${name}.h - Gerado automaticamente" > $hfile
        echo "#pragma once" >> $hfile
        echo "#include \"CoreMinimal.h\"" >> $hfile
        echo "#include \"GameFramework/Actor.h\"" >> $hfile
        echo "" >> $hfile
        echo "class A${name} : public AActor {" >> $hfile
        echo "    GENERATED_BODY()" >> $hfile
        echo "public:" >> $hfile
        echo "    A${name}();" >> $hfile
        echo "    virtual void Tick(float DeltaTime) override;" >> $hfile
        echo "};" >> $hfile

        # CPP
        echo "// ${name}.cpp - Gerado automaticamente" > $cppfile
        echo "#include \"${name}.h\"" >> $cppfile
        echo "" >> $cppfile
        echo "A${name}::A${name}() { PrimaryActorTick.bCanEverTick = true; }" >> $cppfile
        echo "" >> $cppfile
        echo "void A${name}::Tick(float DeltaTime) {" >> $cppfile
        echo "    Super::Tick(DeltaTime);" >> $cppfile
        echo "}" >> $cppfile
    done

    echo "✅ Unreal pronta!"
fi

echo "🎉 Fim!"

````
