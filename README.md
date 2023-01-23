import java.io.FileOutputStream;
import java.util.Scanner;

import org.apache.poi.xssf.usermodel.XSSFSheet;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;

public class ExcelWriter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Please enter Fuel Type: ");
        String fuelType = scanner.nextLine();

        writeToExcel(fuelType);
    }

    public static void writeToExcel(String fuelType) {
        try {
            // Create a new workbook
            XSSFWorkbook workbook = new XSSFWorkbook();

            // Create a new sheet
            XSSFSheet sheet = workbook.createSheet("Fuel Type");

            // Write the input to the sheet
            sheet.createRow(0).createCell(0).setCellValue(fuelType);

            // Save the workbook to a file
            FileOutputStream fileOut = new FileOutputStream("FuelType.xlsx");
            workbook.write(fileOut);
            fileOut.close();

            System.out.println("Fuel Type accepted and written to Excel file successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
