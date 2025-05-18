<div align='center'>

<a href="https://github.com/criszst">
    <a href="#"><img width="100%" src="https://readme-typing-svg.herokuapp.com?font=SUSE&size=30&pause=2000&color=c674ff&center=true&vCenter=true&width=1000&height=60&lines=Howdy,+y'all!!"/>
</a>

A 17-year-old kid who loves studying Big O Notation. Btw, I also enjoy contributing to open sources and exploring more about types on TypeScript. In my spare time, i usually think about new projects and how they can be helpful to someone, which motivates me to study more and more about this small world of technology :)
</div>

---

<br>

 <div align="center">
   <img height="180em" src="https://github-readme-stats.vercel.app/api?username=criszst&show_icons=true&title_color=c674ff&text_color=FFFFFF&icon_color=c674ff&bg_color=0D1017&cache_seconds=23000&hide_border=true" "/>
   <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=criszst&title_color=c674ff&text_color=FFFFFF&icon_color=FFFFFF&bg_color=0D1017&hide_border=true&include_all_commits=true&count_private=true&layout=compact" alt="Top Langs"/>
</div>

<br>

<p align="center">
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=html,css,js,ts,cs,react,nextjs,tailwind,nodejs,express,electron,discordjs,vscode,git,sq" />
  </a>
</p>

<p align="center">
    <a href="https://github.com/criszst/criszst">
      See this readme code
    </a>
</p>

<p align="center">
    <a href="https://github.com/Guilherme-j10/betterQJump/tree/main">
        my fav extension~
    </a>
</p>

</br>
<div style='fontSize: 12px'>
<details>
  <summary>an algorithm inspired by Elimination Gauss that solves linear sistems, which sometimes big o equals to O(n)</summary>

```ts
// A simple (and too "excessive code", cause i create types that are not needed) Elimination Gauss with Ax = B Formula
// ...if this algorithm wasn't o(3), i'd get a tattoo on my face 

type SquareMatrix<Nb extends number> = number[][] & {length: Nb}

function isSquare<Nb extends number>(matrix: number[][], size: Nb): matrix is SquareMatrix<Nb> {
  return matrix.length === size && matrix.every(row => row.length === size)
}

function augmentedMatrix<N extends number>(A: SquareMatrix<N>, B: number[]): number[][] {
  return A.map((row, i) => [...row, B[i]])
}

const applyGaussianElimination = (matrix: number[][]): void => {
  const mLength = matrix.length

  for (let x = 0; x < mLength; x++) {
    const pivot = matrix[x][x]
    
    for (let y = x + 1; y < mLength; y++) {
      let factor = matrix[y][x] / pivot
      for (let z = x; z <= mLength; z++) {
        matrix[y][z] -= factor * matrix[x][z]
      }
    }
  }
}

function backSubstitution(matrix: number[][]): number[] {
  const n = matrix.length;
  const solution = new Array(n).fill(0);

  for (let i = n - 1; i >= 0; i--) {
    let sum = 0
    for (let j = i + 1; j < n; j++) {
      sum += matrix[i][j] * solution[j]
    }
    solution[i] = (matrix[i][n] - sum) / matrix[i][i]
  }

  return solution
}

function linearSystemResult<Nb extends number>(A: SquareMatrix<Nb>, B: number[]): void {
  if (!isSquare(A, 3)) {
    return console.error('Invalid matrix')
  }

  const augmented = augmentedMatrix(A, B)
  applyGaussianElimination(augmented)
  
  return console.log("Solution: ", backSubstitution(augmented))
}

const A = [
  [2, 1, -1],
  [-3, -1, 2],
  [-2, 1, 2]
] as SquareMatrix<3>;

const B = [8, -11, -3];

if (!isSquare(A, 3)) {
  return console.error('Matrix A needed to be equals three rows')
}

linearSystemResult(A, B)

```
</details>
</div>

