# fetch_pdf_files

// fetching PDF file via json key => value pair Dynamically.


key value pair data via json

								$tmp_file = 'uploads/json/commcourt/' . $yr . '.json';

								// Check if the JSON file exists
								if (file_exists($tmp_file)) {
									// Read and decode the JSON data
									$json = file_get_contents($tmp_file);
									$json_data = json_decode($json, true);

									// Initialize the $html variable to store the content
									$html = '';

									foreach ($json_data as $data) {
										$monthNumber = $data['month'];
										$year = $data['year'];
										$link = $data['link'];
										$files = $data['files'];
								
										// Convert month number to month name
										$date = DateTime::createFromFormat('!m', $monthNumber);  // '!' forces PHP to treat the number as a month
										$monthName = $date->format('F');
										$collapseId = 'collapse_' . $monthName . '_' . $year;

										html .= '<div class="card card-default">
													<div class="card-header">
														<h4 class="card-title m-0">
															<a class="accordion-toggle text-color-dark font-weight-bold" data-toggle="collapse" data-parent="#accordion" href="#' . $collapseId . '"> <i class="icons icon-briefcase text-color-primary"></i> Consolidated Report (' . $monthName . ', ' . $year . ') </a>
														</h4>
													</div>
													<div id="' . $collapseId . '" class="collapse" data-parent="#accordion">
														<div class="card-body text-2">
															<p>Consolidated Report of all Districts for the month of ' . $monthName . ', ' . 'my new year' . '.</p>
															<p class="mb-0">';

									foreach ($files as $fileName => $filePath) {
										$fileLink = BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . $link . '/' . $filePath);
										$html .= '<a target="_blank" href="' . $fileLink . '" class="d-block text-color-dark font-weight-semibold pt-2"> ' . $fileName . ' <i class="fas fa-angle-right position-relative top-1 ml-1"></i> </a>';
									}

									// Close the card body and structure
									$html .= '    </p>
												</div>
											</div>
										</div>';
								}

								echo $html;
							}
							?>
       
# JSON FILE TYPE

[{
    "year": "2025",
    "month": "01",
    "link": "public/commCourtData/2025/January",
    "files": [{
        "ClickableName": filethatweneedtoopen.pdf
        "Nstep": "NSTEP.pdf",
        "Random_allocation": "Random_allocation_(e-filing).pdf",
        "Pre-institution_Mediation": "Pre-institution_Mediation.pdf",
        "Summary_of_Commercial_Cases": "Summary_of_Commercial_Cases.pdf",
        "Time_taken_for_disposal": "Time_taken_for_disposal.pdf",
        "e-Filing": "e-Filing(from_e-filing_Branch).pdf",
        "ePayment_of_Court_Fees": "ePayment_of_Court_Fees.pdf",
        "Case_Management_Hearing": "Case_Management_Hearing.pdf",
        "ThreeAdjournment": "ThreeAdjournment.pdf",
        "monthlyreport": "monthlyreport.pdf",
        "Case_Clearance_Rate": "Case_Clearance_Rate.pdf",
        "Sex_Aggregated_Rate": "Sex_Aggregated_Rate.pdf"
}]
},
{
    "year": "2025",
    "month": "02",
    "link": "public/commCourtData/2025/Febuary",
    "files": [{
        "Nstep": "NSTEP.pdf",
        "Random_allocation": "Random_allocation_(e-filing).pdf",
        "Pre-institution_Mediation": "Pre-institution_Mediation.pdf",
        "Summary_of_Commercial_Cases": "Summary_of_Commercial_Cases.pdf",
        "Time_taken_for_disposal": "Time_taken_for_disposal.pdf",
        "e-Filing": "e-Filing(from_e-filing_Branch).pdf",
        "ePayment_of_Court_Fees": "ePayment_of_Court_Fees.pdf",
        "Case_Management_Hearing": "Case_Management_Hearing.pdf",
        "ThreeAdjournment": "ThreeAdjournment.pdf",
        "monthlyreport": "monthlyreport.pdf",
        "Case_Clearance_Rate": "Case_Clearance_Rate.pdf",
        "Sex_Aggregated_Rate": "Sex_Aggregated_Rate.pdf"
}]
},
{
    "year": "2025",
    "month": "03",
    "link": "public/commCourtData/2025/March",
    "files": [{
        "Nstep": "NSTEP.pdf",
        "Random_allocation": "Random_allocation_(e-filing).pdf",
        "Pre-institution_Mediation": "Pre-institution_Mediation.pdf",
        "Summary_of_Commercial_Cases": "Summary_of_Commercial_Cases.pdf",
        "Time_taken_for_disposal": "Time_taken_for_disposal.pdf",
        "e-Filing": "e-Filing(from_e-filing_Branch).pdf",
        "ePayment_of_Court_Fees": "ePayment_of_Court_Fees.pdf",
        "Case_Management_Hearing": "Case_Management_Hearing.pdf",
        "ThreeAdjournment": "ThreeAdjournment.pdf",
        "monthlyreport": "monthlyreport.pdf",
        "Case_Clearance_Rate": "Case_Clearance_Rate.pdf",
        "Sex_Aggregated_Rate": "Sex_Aggregated_Rate.pdf"
}]
},

----------------------------------------------------------------------------------------------------------------------------------------------------------------

# Fetching PDF files via Directory folder Dynamically

            // 	$months = [];
						// 	for ($i = 1; $i <= 12; $i++) {
						// 		// Get the month name using the DateTime class
						// 		$monthName = DateTime::createFromFormat('!m', $i)->format('F');
						// 		$months[] = $monthName;
						// 	}

						// 	$months = array_reverse($months);

						// 	$current_url = $_SERVER['REQUEST_URI'];
						// 	$segments = explode("/", $current_url);
						// 	$year = end($segments); 
						// 	if($year == 'commcourt'){
						// 		$year = date('Y');
						// 	}

						//    foreach ($months as $month) {
						// 	   $collapseId = 'collapse_' . $year . '_' . $month;
								
						// 				echo '<div class="card card-default">
						// 						<div class="card-header">
						// 							<h4 class="card-title m-0">
						// 								<a class="accordion-toggle text-color-dark font-weight-bold" data-toggle="collapse" data-parent="#accordion" href="#' . $collapseId . '">
						// 									<i class="icons icon-briefcase text-color-primary"></i>
						// 									Consolidated Report (' . $month . ', ' . $year . ')
						// 								</a>
						// 							</h4>
						// 						</div>
						// 						<div id="' . $collapseId . '" class="collapse" data-parent="#accordion">
						// 							<div class="card-body text-2">
						// 								<p>Consolidated Report of all Districts for the month of ' . $month . ', ' . $year . '.</p>
						// 								<p class="mb-0">';

						// 			// Construct the directory path dynamically
						// 			$directory = './public/commCourtData/' . $year . '/' . $month;
									
						// 			if (is_dir($directory)) {
						// 				// Get all files in the directory
						// 				$files = scandir($directory);
						// 				foreach ($files as $file) {
						// 					// Exclude the special . and .. directories
						// 					if ($file != '.' && $file != '..') {
						// 						// Use string concatenation correctly
						// 						echo '<a target="_blank" href="'.BASE_URL . 'viewdocuments/'. my_encrypt(BASE_URL .''. $directory . '/' . $file ). '" class="d-block text-color-dark font-weight-semibold pt-2">' . $file . ' <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>';
						// 					}
						// 				}		
						// 			}
							
						// 			echo'          </p>
						// 						</div>
						// 					</div>
						// 				</div>';
						// 		}
							?>
						</div>
					</div>
				</div>
			</div>
			<hr class="">
		</div>
		<!-- <?php include 'private/includes/_footer.php' ?> -->
	</div>

	<?php include 'private/includes/_footer_script.php' ?>

</body>

<script>
	document.getElementById('cirYear').addEventListener('change', function () {
		var selectedYear = this.value;
		//alert(selectedYear);
		if (selectedYear) {
			var newUrl = '<?php echo BASE_URL; ?>commcourt/' + selectedYear;
			window.location.href = newUrl;
		}
	});
</script>

<!-- //Remove it -->
				<div>

				</div>
    </html>
    ------------------------------------------------------------------------------------------
  # Fetch pdf via json - hardcoded NOT Dynamic

<?php
										echo '<div class="card card-default">
							//                 <div class="card-header">
							//                     <h4 class="card-title m-0">
							//                         <a class="accordion-toggle text-color-dark font-weight-bold" data-toggle="collapse" data-parent="#accordion" href="#' . $collapseId . '">
							//                             <i class="icons icon-briefcase text-color-primary"></i>
							//                             Consolidated Report (' . $monthName . ', ' . $row['year'] . ')
							//                         </a>
							//                     </h4>
							                 </div>
							<div id = "'$collapseId.'" .  class="accordion accordion-modern" id="accordion">
							$directory = './public/commCourtData/' . $year . '/' . $month;

								if (is_dir($directory)){
									$files= scandir($directory);
									foreach($files as $file) {
										if($file != '.' && $files != '..'){
											echo '<a target="_blank" href="' . $directory . '/' . $file . '" class="d-block text-color-dark font-weight-semibold pt-2"> ' . $file . ' <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>'
										}
									}

								}
								?>
												
								// Assuming the JSON files are named with the year (e.g., '2024.json')
								$tmp_file = 'uploads/json/commcourt/' . $yr . '.json';
								if (file_exists($tmp_file)) {
									$json = file_get_contents($tmp_file);
									$json_data = json_decode($json, true);

									// Sort the $json_data array by the 'month' field in descending order
									usort($json_data, function ($a, $b) {
										return $b['month'] - $a['month']; // For descending order
									});

									if (isset($json_data)) {
										foreach ($json_data as $index => $row) {
											$dateObj = DateTime::createFromFormat('!m', $row['month']);
											$monthName = $dateObj->format('F');
											$collapseId = 'collapse' . $index;

											// Check if the month is December 2024 or later
											$isFutureReport = ($row['year'] >= 2024 && $row['month'] >= 12);

											// Displaying the statistical data for each month
											echo '<div class="card card-default">
                        							<div class="card-header">
                            							<h4 class="card-title m-0">
                                							<a class="accordion-toggle text-color-dark font-weight-bold" data-toggle="collapse" data-parent="#accordion" href="#' . $collapseId . '">
                                    							<i class="icons icon-briefcase text-color-primary"></i>
                                    								Consolidated Report (' . $monthName . ', ' . $row['year'] . ')
                                							</a>
                            							</h4>
                        							</div>
                        							<div id="' . $collapseId . '" class="collapse" data-parent="#accordion">
                            							<div class="card-body text-2">
                                							<p>Consolidated Report of all Districts for the month of ' . $monthName . ', ' . $row['year'] . '.</p>
                                 							<p class="mb-0"> 
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][0]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> NSTEP <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][1]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Random allocation <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][2]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Pre-institution Mediation <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][3]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Summary of Commercial Cases <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][4]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Time taken for disposal <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
						 						<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][5]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> e-Filing <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][6]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> ePayment of Court Fees <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][7]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Case Management Hearing <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][8]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Three Adjournment <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][9]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Monthly Report <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>
												</p>';

											// Add the case clearance rate report link for December 2024 and future reports
											if (($row['year'] > 2024 || ($row['year'] == 2024 && $row['month'] >= 12)) && isset($row['files'][10])) {
												echo '<a target="_blank" href="' . BASE_URL . 'viewdocuments/' . my_encrypt(BASE_URL . '' . $row['link'] . '/' . $row['files'][10]) . '" class="d-block text-color-dark font-weight-semibold pt-2"> Case Clearance Rate Report <i class="fas fa-angle-right position-relative top-1 ml-1"></i></a>';
											}
											echo '   </div>
                        					</div>
                    					</div>';
										}
									}
								}
								?>
							</div>

						</div>
					</div>
				</div>
			</div>
			<hr class="">
		</div>
		<!-- <?php include 'private/includes/_footer.php' ?> -->
	</div>

	<?php include 'private/includes/_footer_script.php' ?>

</body>

<script>
	document.getElementById('cirYear').addEventListener('change', function () {
		var selectedYear = this.value;
		//alert(selectedYear);
		if (selectedYear) {
			var newUrl = '<?php echo BASE_URL; ?>commcourt/' + selectedYear;
			window.location.href = newUrl;
		}
	});
</script>



    

