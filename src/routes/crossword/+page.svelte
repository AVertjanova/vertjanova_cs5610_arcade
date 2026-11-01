<header>
  <h1>Simple Crossword Game</h1>
</header>

<main>
  <div class="crossword-page">
    <table class="table-container">
      <tbody>
        <tr>
          <td class="dark-square"></td>
          <td class="crossword-square"
            >1
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 1, column 2, 1 down, 1 across"
            />
          </td>
          <td class="crossword-square"
            >2
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 1, column 3, 2 down"
            />
          </td>
          <td class="crossword-square"
            >3
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 1, column 4, 3 down"
            />
          </td>
          <td class="crossword-square"
            >4
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 1, column 5, 4 down"
            />
          </td>
        </tr>
        <tr>
          <td class="dark-square"></td>
          <td class="crossword-square"
            >5
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 2, column 2, 5 across"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 2, column 3"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 2, column 4"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 2, column 5"
            />
          </td>
        </tr>
        <tr>
          <td class="crossword-square"
            >6
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 3, column 1, 6 across"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 3, column 2"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 3, column 3"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 3, column 4"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 3, column 5"
            />
          </td>
        </tr>
        <tr>
          <td class="crossword-square"
            >7
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 4, column 1, 7 across"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 4, column 2"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 4, column 3"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 4, column 4"
            />
          </td>
          <td class="dark-square"></td>
        </tr>
        <tr>
          <td class="crossword-square"
            >8
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 5, column 1, 8 across"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 5, column 2"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 5, column 3"
            />
          </td>
          <td class="crossword-square">
            <input
              class="cross-input"
              type="text"
              maxlength="1"
              aria-label="Row 5, column 4"
            />
          </td>
          <td class="dark-square"></td>
        </tr>
      </tbody>
    </table>

    <div class="clues">
      <h2>Across:</h2>
      <details>
        <summary>1. Sail right by</summary>
        <p>pass</p>
      </details>
      <details>
        <summary>5. __ bean (also the capital city of Peru)</summary>
        <p>lima</p>
      </details>
      <details>
        <summary>6. "__ on a true story" (movie prase)</summary>
        <p>based</p>
      </details>
      <details>
        <summary>7. Los Angeles college, for short</summary>
        <p>UCLA</p>
      </details>
      <details>
        <summary>8. Forest animal with antlers</summary>
        <p>deer</p>
      </details>

      <h2>Down:</h2>
      <details>
        <summary>1. Spot or location</summary>
        <p>place</p>
      </details>
      <details>
        <summary>2. Walkway between rows of seats</summary>
        <p>aisle</p>
      </details>
      <details>
        <summary>3. Spread thickly around, as peanutbutter on bread</summary>
        <p>smear</p>
      </details>
      <details>
        <summary>4. Not happy</summary>
        <p>sad</p>
      </details>
      <details>
        <summary>6. Close pal</summary>
        <p>bud</p>
      </details>
    </div>
  </div>
</main>

<!--Crossword from minicrossword.com-->

<style>
  :root {
    --cross-square: 5rem;
  }

  .crossword-page {
    display: flex;
    flex-wrap: wrap;
    gap: 3rem;
  }

  @media (max-width: 800px) {
    .crossword-page {
      flex-direction: column;
    }
  }

  .clues {
    color: var(--dark);
    width: 26rem;
  }

  .table-container {
    display: grid;
    grid-template-columns: repeat(5, var(--cross-square));
    border: 1px var(--dark);
  }

  tbody,
  tr {
    display: contents;
  }

  .crossword-square {
    background-color: var(--light);
    color: var(--dark);
    border: 1px solid var(--dark);
    height: var(--cross-square);
    width: var(--cross-square);
    display: grid;
    justify-content: center;
    align-content: end;
    font-size: 0.5rem;
  }

  .cross-input {
    background-color: var(--light);
    height: 4rem;
    width: 4.5rem;
    font-size: 3rem;
    justify-content: center;
    align-items: last baseline;
    border: none;
  }

  .dark-square {
    background-color: var(--dark);
    color: var(--dark);
    border: 1px solid var(--light);
    height: var(--cross-square);
    width: var(--cross-square);
  }
</style>
