import java.util.Random;

public class RandomCardSelection {
    public static void main(String[] args) {
        int[] valDeck = new int[52];
        for (int i = 0; i < valDeck.length; i++) {
            valDeck[i] = i;
        }

        shuffleDeck(valDeck);

        // Selecting four random cards
        for (int i = 0; i < 4; i++) {
            int cardIndex = valDeck[i];
            int suit = cardIndex / 13;
            int rank = cardIndex % 13;

            String suitName = getSuitName(suit);
            String rankName = getRankName(rank);

            System.out.println("Card " + (i + 1) + ": " + rankName + " of " + suitName);
        }
    }

    public static void shuffleDeck(int[] deck) {
        Random random = new Random();
        for (int i = deck.length - 1; i > 0; i--) {
            int j = random.nextInt(i + 1);
            int temp = deck[i];
            deck[i] = deck[j];
            deck[j] = temp;
        }
    }

    public static String getSuitName(int suit) {
        switch (suit) {
            case 0:
                return "Spades";
            case 1:
                return "Hearts";
            case 2:
                return "Diamonds";
            case 3:
                return "Clubs";
            default:
                return "Invalid suit";
        }
    }

    public static String getRankName(int rank) {
        switch (rank) {
            case 0:
                return "Ace";
            case 10:
                return "Jack";
            case 11:
                return "Queen";
            case 12:
                return "King";
            default:
                return String.valueOf(rank + 1);
        }
    }
}
