# Teoría: Bits y Cúbits (Qubits)

Este documento explica la teoría fundamental presentada en el notebook "02. Bits y Cúbits.ipynb", cubriendo desde los conceptos clásicos de bits hasta los fundamentos de la computación cuántica.

## Tabla de Contenidos

1. [Bits Clásicos y Puertas Clásicas](#1-bits-clásicos-y-puertas-clásicas)
2. [Bits Cuánticos (Cúbits)](#2-bits-cuánticos-cúbits)
3. [Puertas Cuánticas](#3-puertas-cuánticas)
4. [Medición de Estados Cuánticos](#4-medición-de-estados-cuánticos)

---

## 1. Bits Clásicos y Puertas Clásicas

### 1.1 Representación Vectorial de Bits Clásicos

Un bit clásico puede representarse como un vector bidimensional con probabilidades que suman 1:

```
|b⟩ = [p₀; p₁]
```

donde `p₀, p₁ ∈ {0,1}` y `p₀ + p₁ = 1`

Los estados base son:
- **|0⟩ = [1; 0]** - representa el bit 0
- **|1⟩ = [0; 1]** - representa el bit 1

### 1.2 Sistemas Multi-bit

Para representar múltiples bits, se utiliza el producto tensorial (⊗):

```
|ab⟩ = |a⟩ ⊗ |b⟩ = [a₀b₀; a₀b₁; a₁b₀; a₁b₁]
```

Un sistema de n bits se representa como:

```
|B⟩ = Σᵢ pᵢ|i⟩  donde Σpᵢ = 1
```

### 1.3 Puertas Clásicas como Matrices

Las puertas lógicas clásicas pueden representarse como operadores matriciales:

**Puerta NOT:**
```
NOT = [0 1]
      [1 0]
```

**Puerta AND:**
```
AND = [1 1 1 0]
      [0 0 0 1]
```

**Puerta OR:**
```
OR = [1 0 0 0]
     [0 1 1 1]
```

### 1.4 Computación Reversible

#### Principio de Landauer
Borrar información tiene un costo energético mínimo proporcional a kT ln 2, donde:
- k es la constante de Boltzmann
- T es la temperatura

#### Puertas Reversibles

**CNOT (Controlled-NOT):**
```
CNOT = [1 0 0 0]
       [0 0 0 1]
       [0 0 1 0]
       [0 1 0 0]
```

La puerta CNOT es su propia inversa: `CNOT = CNOT⁻¹`

**Puertas Toffoli y Fredkin:** Permiten convertir operaciones irreversibles en reversibles usando bits ancilla (auxiliares).

---

## 2. Bits Cuánticos (Cúbits)

### 2.1 Vector de Estado

Un cúbit es una generalización de un bit clásico al espacio complejo:

```
|ψ⟩ = [a₀; a₁]
```

donde:
- `aᵢ ∈ ℂ` (números complejos)
- `|a₀|² + |a₁|² = 1` (condición de normalización)

En la base canónica (computacional):

```
|ψ⟩ = a₀|0⟩ + a₁|1⟩
```

donde `|a₀|²` y `|a₁|²` representan las probabilidades de medir 0 y 1, respectivamente.

### 2.2 Bases Importantes

#### Base Computacional
```
|0⟩ = [1; 0]
|1⟩ = [0; 1]
```

#### Base X (Hadamard)
```
|+⟩ = 1/√2(|0⟩ + |1⟩)
|-⟩ = 1/√2(|0⟩ - |1⟩)
```

#### Base Y
```
|+i⟩ = 1/√2(|0⟩ + i|1⟩)
|-i⟩ = 1/√2(|0⟩ - i|1⟩)
```

### 2.3 Esfera de Bloch

La esfera de Bloch es una representación geométrica tridimensional del estado de un cúbit único.

#### Parametrización Esférica

Cualquier estado de un cúbit puede escribirse como:

```
|ψ⟩ = cos(θ/2)|0⟩ + e^(iφ)sin(θ/2)|1⟩
```

donde:
- `θ ∈ [0, π]` - ángulo polar
- `φ ∈ [0, 2π)` - ángulo azimutal

#### Coordenadas Cartesianas

La representación en coordenadas cartesianas de la esfera de Bloch es:

```
rₓ = sin θ cos φ
rᵧ = sin θ sin φ
r_z = cos θ
```

#### Puntos Especiales
- **Polo Norte**: |0⟩ (θ = 0)
- **Polo Sur**: |1⟩ (θ = π)
- **Ecuador**: Estados de superposición como |+⟩, |-⟩, |+i⟩, |-i⟩

### 2.4 Fase Global vs. Fase Relativa

#### Fase Global
```
e^(iφ₀)|ψ⟩ ≡ |ψ⟩
```
La fase global no tiene significado físico; los estados son equivalentes.

#### Fase Relativa
```
|ψ⟩ = a₀|0⟩ + e^(iφ)a₁|1⟩
```
La fase relativa `e^(iφ)` entre amplitudes tiene significado físico y afecta las mediciones.

### 2.5 Sistemas Multi-Cúbit

Un sistema de n cúbits se representa como:

```
|ψ⟩ = Σᵢ₌₀^(2ⁿ-1) aᵢ|i⟩
```

donde `Σᵢ |aᵢ|² = 1`

Para sistemas compuestos, se usa el producto tensorial:

```
|ψ⟩ = |ψ₁⟩ ⊗ |ψ₂⟩
```

### 2.6 Propiedades Fundamentales

#### Espacio de Hilbert
El espacio de estados cuánticos es un espacio vectorial complejo con producto interno (2D para un cúbit único).

#### Normalización
Todos los estados cuánticos deben satisfacer `||ψ⟩|| = 1`.

#### Amplitudes de Probabilidad
Las amplitudes son números complejos cuyo módulo al cuadrado da las probabilidades.

### 2.7 Restricciones Cuánticas

1. **Teorema de No-Clonación**: No es posible copiar perfectamente estados cuánticos desconocidos
2. **Medición Destructiva**: La medición colapsa el estado
3. **Colapso de Superposición**: La superposición colapsa al medir

---

## 3. Puertas Cuánticas

### 3.1 Matrices de Pauli (Puertas de 1-Cúbit)

**Puerta X (NOT Cuántica):**
```
σₓ = [0 1]
     [1 0]
```
Intercambia |0⟩ ↔ |1⟩

**Puerta Y:**
```
σᵧ = [0  -i]
     [i   0]
```

**Puerta Z:**
```
σ_z = [1   0]
      [0  -1]
```
Aplica un cambio de fase: |1⟩ → -|1⟩

### 3.2 Puerta Hadamard

```
H = 1/√2 [1   1]
         [1  -1]
```

**Efectos importantes:**
- `H|0⟩ = |+⟩ = 1/√2(|0⟩ + |1⟩)` - crea superposición
- `H|1⟩ = |-⟩ = 1/√2(|0⟩ - |1⟩)`
- `H|+⟩ = |0⟩`
- `H|-⟩ = |1⟩`

La puerta Hadamard es su propia inversa: `H² = I`

### 3.3 Puertas de Rotación

Las puertas de rotación realizan rotaciones alrededor de los ejes de la esfera de Bloch:

**Rotación alrededor del eje X:**
```
Rₓ(φ) = [cos(φ/2)    -i·sin(φ/2)]
        [-i·sin(φ/2)  cos(φ/2)   ]
```

**Rotación alrededor del eje Y:**
```
Rᵧ(φ) = [cos(φ/2)   -sin(φ/2)]
        [sin(φ/2)    cos(φ/2) ]
```

**Rotación alrededor del eje Z:**
```
R_z(φ) = [e^(-iφ/2)    0      ]
         [0          e^(iφ/2)  ]
```

### 3.4 Walsh-Hadamard

La transformada Walsh-Hadamard para n cúbits es:

```
H^⊗ⁿ = H ⊗ H ⊗ ... ⊗ H  (n veces)
```

Crea superposición uniforme de todos los estados:

```
H^⊗ⁿ|0⟩^⊗ⁿ = 1/√(2ⁿ) Σᵢ₌₀^(2ⁿ-1) |i⟩
```

---

## 4. Medición de Estados Cuánticos

### 4.1 Postulado de Medición

Cuando se mide un estado:

```
|ψ⟩ = a₀|0⟩ + a₁|1⟩
```

Se obtiene:
- **Resultado 0** con probabilidad `|a₀|²`, y el estado colapsa a `|0⟩`
- **Resultado 1** con probabilidad `|a₁|²`, y el estado colapsa a `|1⟩`

### 4.2 Observables

Un observable es un operador Hermitiano cuyos eigenvalores representan los posibles resultados de medición.

**Mediciones en Base de Pauli:**
- **Medición Z** (base computacional): observable σ_z
- **Medición X** (base Hadamard): observable σₓ
- **Medición Y**: observable σᵧ

### 4.3 Valor Esperado

El valor esperado de un observable A en el estado |ψ⟩ es:

```
⟨A⟩ = ⟨ψ|A|ψ⟩
```

### 4.4 Observables como Descomposición de Pauli

Cualquier observable puede expresarse como combinación lineal de productos tensoriales de las matrices de Pauli:

```
M = Σᵢ cᵢPᵢ
```

donde `Pᵢ` son productos tensoriales de `{𝕀, σₓ, σᵧ, σ_z}`

**Ejemplo:**
```
M = 0.5·X⊗I⊗X - 3·I⊗Y⊗Z + 2·X⊗X⊗X
```

### 4.5 Implementación Práctica con Qiskit

#### Creación de Estados
```python
from qiskit.quantum_info import Statevector

# Crear estado |ψ⟩ = a₀|0⟩ + a₁|1⟩
estado = Statevector([a0, a1])
```

#### Visualización
```python
# Mostrar en notación LaTeX
estado.draw('latex')

# Visualizar en esfera de Bloch
from qiskit.visualization import plot_bloch_multivector
plot_bloch_multivector(estado)
```

#### Definición de Observables
```python
from qiskit.quantum_info import SparsePauliOp

# Definir observable M
M = SparsePauliOp.from_list([
    ("XIX", 0.5),   # 0.5·X⊗I⊗X
    ("IYZ", -3),    # -3·I⊗Y⊗Z
    ("XXX", 2)      # 2·X⊗X⊗X
])
```

---

## Conceptos Clave para Recordar

1. **Los cúbits generalizan los bits clásicos** usando amplitudes complejas en lugar de probabilidades reales.

2. **La esfera de Bloch** proporciona una representación geométrica intuitiva de estados de cúbit único.

3. **La fase relativa** entre amplitudes es físicamente significativa, aunque la fase global no lo es.

4. **Las puertas cuánticas** son operadores unitarios que preservan la normalización.

5. **La medición es probabilística** y colapsa la superposición al estado medido.

6. **El teorema de no-clonación** y otras restricciones cuánticas fundamentales limitan qué operaciones son posibles.

7. **Los observables Hermitianos** representan cantidades medibles con eigenvalores reales.

8. **La computación reversible** es esencial tanto en la computación clásica eficiente como en la cuántica.

---

## Referencias

Este documento está basado en el contenido del notebook "02. Bits y Cúbits.ipynb" del repositorio CUANTICA, que proporciona una introducción matemática rigurosa a los fundamentos de la computación cuántica.
